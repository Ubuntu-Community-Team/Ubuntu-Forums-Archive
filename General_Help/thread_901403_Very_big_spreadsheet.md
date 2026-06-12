---
title: "Very big spreadsheet"
date: 2008-08-26
forum: General Help
---

### Post by blackind on 2008-08-26
Hello!

 I have a .txt file with 2 columns and about 155000 rows.
 I just want to plot the data on a X-Y axis. 
So I put them in OpenOffice Spreadsheet but the limit is about 65000 rows.
I tried software such as labplot and qtiplot but they seem to take such a long time to build the diagram, that i couldn't wait to see it finished!
The only software that worked well was kst. 
But I can't find a way to do mathematical actions over the data like in Excel, OpenOffice Spreadsheet etc. 
Any suggestions?

---

### Post by xravexheavenx on 2008-08-26
You could always drop it into a SQL database.

---

### Post by blackind on 2008-08-26
Well, I've never worked with access or similar programs...

---

### Post by blackind on 2008-08-26
Anyway, I tried to import the data by opening the txt file but I have this message:
"The maximum number of rows has been exceeded. Excessn rows were not imported"

---

### Post by linux_tech on 2008-08-26
Spreadsheet programs are really only meant to handle a certain # of records.
One main reason is performance.  A database can handle many more records.
So to continue to work with the file it would be best to either convert it to a database or split the file up into 3 or 4 smaller files.

To open the file initially, you may wish to check this as it has a method to open large excel files. 
[http://www.cpearson.com/excel/ImportBigFiles.aspx](http://www.cpearson.com/excel/ImportBigFiles.aspx)
[http://odf-converter.sourceforge.net/download.html](http://odf-converter.sourceforge.net/download.html)

---

### Post by blackind on 2008-08-26
Thanks, this was what i was looking for!!

---

### Post by HermanAB on 2008-08-26
Gnuplot maybe.

---

### Post by gergn on 2010-04-08
You can use Gnumeric 1.9.9. Standard sheets have at most 65.536 rows. But by right-clicking on the sheet name you can increase the maximum of rows to 8M.

---

### Post by eriktheblu on 2010-04-08
Databases are really the way to go when you start dealing with large amounts of data.

If you're going to be doing this sort of thing often, I would suggest familiarizing yourself with one.

I learned Access a couple years back and now I rarely use Excel for data analysis.

---

### Post by tgalati4 on 2010-04-08
gnuplot can handle really large data sets.

sudo apt-get install gnuplot

man gnuplot

---

