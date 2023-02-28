### Создадим таблицу c жанрами и заполним ее.  
create table dbo.style  
(  
	styleId int primary key,  
	styleName nvarchar(128) not null  
)  

insert into dbo.Employee(styleId, styleName) values (1, 'Rock')  
insert into dbo.Employee(styleId, styleName) values (2, 'Techno')  
insert into dbo.Employee(styleId, styleName) values (3, 'Trance')  


### Создадим таблицу c музыкантами и заполним ее.  
create table dbo.musican  
(  
	musicanId int primary key,  
	musicanName nvarchar(128) not null  
)  

insert into dbo.Employee(musicanId, musicanName) values (1, 'Metallica')  
insert into dbo.Employee(musicanId, musicanName) values (2, 'Alter Bridge')  
insert into dbo.Employee(musicanId, musicanName) values (3, 'Gorky Park')  

### Создадим таблицу StyleMusican и заполним ее.  
create table dbo.StyleMusican  
(  
	musicanId int foreign key references dbo.musican(musicanId),  
	styleId int foreign key references dbo.style(styleId),  
	primary key(musicanId, styleId)  
)  

insert into dbo.StyleMusican(styleId, musicanId) values (1, 1)  
insert into dbo.StyleMusican(styleId, musicanId) values (1, 2)  
insert into dbo.StyleMusican(styleId, musicanId) values (2, 3)  
insert into dbo.StyleMusican(styleId, musicanId) values (3, 3)  

### Создадим таблицу c альбомами и заполним ее.  
create table dbo.albom  
(  
	albomId int primary key,  
	albomName nvarchar(128) not null  
)  

insert into dbo.Employee(albomId, albomName) values (1, 'Blaco Album')  
insert into dbo.Employee(albomId, albomName) values (2, 'Load')   

### Создадим таблицу MusicanAlbum и заполним ее.  
create table dbo.MusicanAlbum  
(  
	musicanId int foreign key references dbo.musican(musicanId),  
	albumId int foreign key references dbo.album(albumId),  
	primary key(musicanId, albumId)  
)  

insert into dbo.MusicanAlbum(albumId, musicanId) values (1, 1)  
insert into dbo.MusicanAlbum(albumId, musicanId) values (1, 2)  

### Создадим таблицу с трэками.  
create table dbo.track  
(  
	trackId int primary key,  
	trackName nvarchar(128) not null  
  trackDuration nvarchar(128) not null  
  albumId int foreign key references dbo.album(albumId)   
)  

### Создадим таблицу со сборниками.  
create table dbo.sbornik  
(  
	sbornikId int primary key,  
	sbornikName nvarchar(128) not null  
  sbornikDate nvarchar(128) not null   
)  

### Создадим таблицу TrackSbornik и заполним ее.  
create table dbo.TrackSbornik  
(  
	sbornikId int foreign key references dbo.sbornik(sbornikId),  
	trackId int foreign key references dbo.track(trackId),  
	primary key(trackId, sbornikId)  
)  

insert into dbo.TrackSbornik(trackId, sbornikId) values (1, 1)  
insert into dbo.TrackSbornik(trackId, sbornikId) values (1, 2) 
