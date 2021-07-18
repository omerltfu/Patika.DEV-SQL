# Patika.DEV-SQL
## ODEV 1
### -film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
`SELECT title,description FROM film ;`

### -film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
`SELECT *from film
WHERE length > 60 AND length < 75;`

### -film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
`SELECT * from film
WHERE rental_rate = 0.99 and replacement_cost = 12.99 OR replacement_cost = 28.99;`

### -customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
`SELECT * FROM customer
WHERE first_name = 'Mary';` 

bu sorguyu yazarak Mary adlı kişinin ikinci adının Smith olduğu anlaşılmakta
### -film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
`SELECT * FROM film
WHERE Not length > 50 AND NOT ( rental_rate = 2.99 or rental_rate = 4.99)`
*****************************************************************************

## ODEV 2
### 1-film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla
sıralayınız ( BETWEEN - AND yapısını kullanınız.)
`SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;`

### 2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

`SELECT first_name , last_name FROM actor
WHERE first_name IN('Penelope','Nick','Ed');`

### 3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.
(IN operatörünü kullanınız.)

`SELECT * FROM film
WHERE  (rental_rate IN (0.99,2.99,4.99)) AND (replacement_cost IN (12.99,15.99,28.99))`
*****************************************************************************************************
## ODEV 3
### 1-country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
`SELECT country FROM country
WHERE country LIKE 'A%a';`

### 2-country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
`SELECT country FROM country
WHERE length(country) >= 6 and country LIKE '%n';`

### 3- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
`SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%';`

### 4-film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

`SELECT * FROM film
WHERE title LIKE 'C%' AND (length > 90 AND rental_rate = 2.99);`
******************************************************************************************************
## ODEV 4

### 1-film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
`SELECT DISTINCT replacement_cost FROM film;`

### 2-film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
`SELECT COUNT(DISTINCT replacement_cost) FROM film;`

### 3-film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
`SELECT COUNT(*) FROM film 
WHERE title = 'T%' AND rating = 'G';`

### 4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
`SELECT COUNT(*) FROM country
WHERE length(country) = 5;`

### 5-city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
`SELECT COUNT(*) FROM city
WHERE city ILIKE '%r'`
******************************************************************************************
## ODEV 5
### 1-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
`SELECT * from film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5 ;`

### 2-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
`SELECT * from film
WHERE title LIKE '%n'
ORDER by length
OFFSET 5
LIMIT 5;`

### 3-customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
`SELECT * from customer
WHERE store_id = 1
ORDER BY last_name
LIMIT 4	;`
******************************************************************************************************

## ODEV 6

### 1-film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
`SELECT ROUND(AVG(rental_rate),4) FROM film;`

### 2-film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
`SELECT COUNT(*) from film
WHERE title LIKE 'C%';`

### 3-film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
`SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;`

### 4-film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
`SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;`
****************************************************************************************************
## ODEV 7

### 1-film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
`SELECT rating FROM film
GROUP BY rating;`

### 2-film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
` SELECT replacement_cost , COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;`

### 3-customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
`SELECT store_id , COUNT(*) FROM customer
GROUP BY store_id;`

### 4-city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
`SELECT country_id , COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) desc
LIMIT 1`
********************************************************************************************************
## ODEV 8

### 1-test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

`Create table employee (
	id int ,
	name varchar(50),
	birthday DATE ,
	email varchar(100)
);`

### 2-Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
`insert into employee (id, name, birthday, email) values (1, 'Winthrop Leneham', '2013-11-21', 'wleneham0@tamu.edu');
insert into employee (id, name, birthday, email) values (2, 'Laurie Rainford', '2011-01-24', 'lrainford1@ca.gov');
insert into employee (id, name, birthday, email) values (3, 'Griffy Pleass', '2013-01-12', 'gpleass2@reddit.com');
insert into employee (id, name, birthday, email) values (4, 'Nannie MacGillivray', '2008-02-27', 'nmacgillivray3@naver.com');
insert into employee (id, name, birthday, email) values (5, 'Phyllis Sibbs', '2015-12-25', 'psibbs4@google.fr');
insert into employee (id, name, birthday, email) values (6, 'Curran Duffield', '2012-05-17', 'cduffield5@posterous.com');
insert into employee (id, name, birthday, email) values (7, 'Calv Tittershill', '2006-12-12', 'ctittershill6@reverbnation.com');
insert into employee (id, name, birthday, email) values (8, 'Porty Yeoland', '2018-11-27', 'pyeoland7@cbsnews.com');
insert into employee (id, name, birthday, email) values (9, 'Phip Gravener', '2013-05-29', 'pgravener8@cnn.com');
insert into employee (id, name, birthday, email) values (10, 'Etti Pallas', '2017-03-15', 'epallas9@issuu.com');
insert into employee (id, name, birthday, email) values (11, 'Hugh Jersh', '2002-06-06', 'hjersha@wsj.com');
insert into employee (id, name, birthday, email) values (12, 'Odille Pentlow', '2020-09-03', 'opentlowb@cdbaby.com');
insert into employee (id, name, birthday, email) values (13, 'Milzie Duckitt', '2004-12-15', 'mduckittc@java.com');
insert into employee (id, name, birthday, email) values (14, 'Montague Twelvetree', '2001-10-22', 'mtwelvetreed@si.edu');
insert into employee (id, name, birthday, email) values (15, 'Prudence Roxbee', '2019-08-13', 'proxbeee@nationalgeographic.com');
insert into employee (id, name, birthday, email) values (16, 'Wenonah Jenk', '2011-05-23', 'wjenkf@chron.com');
insert into employee (id, name, birthday, email) values (17, 'Gideon Seggie', '2004-10-04', 'gseggieg@geocities.jp');
insert into employee (id, name, birthday, email) values (18, 'Dorise MacGahey', '2001-06-16', 'dmacgaheyh@blog.com');
insert into employee (id, name, birthday, email) values (19, 'Hansiain Keen', '2008-04-03', 'hkeeni@cmu.edu');
insert into employee (id, name, birthday, email) values (20, 'Herculie Kelloch', '2013-09-20', 'hkellochj@thetimes.co.uk');
insert into employee (id, name, birthday, email) values (21, 'Marisa Brittles', '2015-08-16', 'mbrittlesk@europa.eu');
insert into employee (id, name, birthday, email) values (22, 'Lem Rotter', '2016-06-04', 'lrotterl@hp.com');
insert into employee (id, name, birthday, email) values (23, 'Traver Mensler', '2011-01-10', 'tmenslerm@t.co');
insert into employee (id, name, birthday, email) values (24, 'Querida Johnke', '2009-08-01', 'qjohnken@oaic.gov.au');
insert into employee (id, name, birthday, email) values (25, 'Ginelle Filippi', '2004-08-12', 'gfilippio@newyorker.com');
insert into employee (id, name, birthday, email) values (26, 'Pegeen Hamblett', '2015-04-25', 'phamblettp@cmu.edu');
insert into employee (id, name, birthday, email) values (27, 'Kellen Busby', '2001-12-16', 'kbusbyq@webeden.co.uk');
insert into employee (id, name, birthday, email) values (28, 'Burgess Skeffington', '2020-07-10', 'bskeffingtonr@scientificamerican.com');
insert into employee (id, name, birthday, email) values (29, 'Nobe Dominey', '2001-06-19', 'ndomineys@blinklist.com');
insert into employee (id, name, birthday, email) values (30, 'Kaylee Blum', '2007-01-12', 'kblumt@engadget.com');
insert into employee (id, name, birthday, email) values (31, 'Gael Fosdike', '2011-07-09', 'gfosdikeu@trellian.com');
insert into employee (id, name, birthday, email) values (32, 'Benita Kobsch', '2008-01-04', 'bkobschv@columbia.edu');
insert into employee (id, name, birthday, email) values (33, 'Alexei Kermit', '2002-12-26', 'akermitw@hostgator.com');
insert into employee (id, name, birthday, email) values (34, 'Lynde Guerrieri', '2010-11-30', 'lguerrierix@loc.gov');
insert into employee (id, name, birthday, email) values (35, 'Antony D''Oyly', '2014-08-23', 'adoylyy@blog.com');
insert into employee (id, name, birthday, email) values (36, 'Kylynn Kellough', '2013-08-25', 'kkelloughz@walmart.com');
insert into employee (id, name, birthday, email) values (37, 'Ainslee Goodbar', '2002-07-07', 'agoodbar10@blogs.com');
insert into employee (id, name, birthday, email) values (38, 'Baird Meuse', '2003-05-23', 'bmeuse11@nydailynews.com');
insert into employee (id, name, birthday, email) values (39, 'Wyn Drugan', '2018-01-31', 'wdrugan12@mozilla.com');
insert into employee (id, name, birthday, email) values (40, 'Nerte Chaff', '2004-06-22', 'nchaff13@archive.org');
insert into employee (id, name, birthday, email) values (41, 'Winny Laurence', '2011-01-06', 'wlaurence14@tripadvisor.com');
insert into employee (id, name, birthday, email) values (42, 'Albrecht Poxon', '2002-10-18', 'apoxon15@csmonitor.com');
insert into employee (id, name, birthday, email) values (43, 'Korney Raistrick', '2012-09-04', 'kraistrick16@stumbleupon.com');
insert into employee (id, name, birthday, email) values (44, 'Janek Loude', '2017-04-26', 'jloude17@engadget.com');
insert into employee (id, name, birthday, email) values (45, 'Carina Chantree', '2021-05-15', 'cchantree18@wix.com');
insert into employee (id, name, birthday, email) values (46, 'Rhetta MacCosto', '2019-12-10', 'rmaccosto19@army.mil');
insert into employee (id, name, birthday, email) values (47, 'Court Fee', '2015-12-26', 'cfee1a@51.la');
insert into employee (id, name, birthday, email) values (48, 'Jude Gallardo', '2002-04-01', 'jgallardo1b@hhs.gov');
insert into employee (id, name, birthday, email) values (49, 'Lyn Carthy', '2010-01-28', 'lcarthy1c@tripod.com');
insert into employee (id, name, birthday, email) values (50, 'Bax Fallowfield', '2020-11-26', 'bfallowfield1d@harvard.edu');`

### 3-Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
`UPDATE employee SET name ='Omer Lutfu' WHERE id = 1;
UPDATE employee SET email = 'omer@lutfu.com' WHERE name ='Omer Lutfu';
UPDATE employee SET birthday = '1997-08-14' WHERE email = 'omer@lutfu.com';
UPDATE employee SET name ='Fatih' , email='fatih@sultan.com' WHERE name = 'Laurie Rainford';
UPDATE employee SET birthday = '2012-10-10' , name = 'Audrey Hillor' WHERE id = 5;`

### 4-Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
`DELETE from employee WHERE id = 5;
DELETE FROM employee WHERE name = 'Omer Lutfu';
DELETE FROM employee WHERE birthday = '2018-11-27';
DELETE FROM employee WHERE email = 'fatih@sultan.com';
DELETE FROM employee WHERE id = 24;
`
