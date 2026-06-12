---
title: "Errorinfo:can't find package sqlite3"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by anbunathanr on 2009-03-20
While executing TCL commands, i am getting this error:
Errorinfo:can't find package sqlite3

Note: The TCL code is attached

package require Tcl 8.4
package versions sqlite
package require sqlite3
sqlite3 db1 ./home/anbu/Desktop/linux/TCL/testdb
db1 close

---

### Post by Anthon on 2009-03-20
Try:
  sudo apt-get install sqlite3
and see if that helps

---

### Post by anbunathanr on 2009-03-20
I am getting the following error:

root@anbu-desktop:/usr/lib# sudo apt-get install sqlite3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sqlite3 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

---

### Post by anbunathanr on 2009-03-20
I am not sure about what to do

---

### Post by Anthon on 2009-03-20
Seems tcl doesn't come with batteries included (sorry I am more of a Python guy).
There is a another package that might be missing, so once more try: 
sudo apt-get install libsqlite3-tcl

Do you have a minimal tcl program that creates this error?

---

### Post by sudipta_cht on 2009-04-28
Okay, so here is the link that says how to make tcl work with sqlite3:
[http://www.tcl.tk/community/tcl2004/Papers/D.RichardHipp/drh.html]("http://www.tcl.tk/community/tcl2004/Papers/D.RichardHipp/drh.html")]

Unfortunately, it doesn't work. Instead, I had to do the following:
[INDENT]
#!/usr/bin/tclsh
#package require sqlite3

exec /usr/bin/sqlite3 db1 {CREATE TABLE geom1(rect_id , x0 , y0 , x1 , y1 )}

exec /usr/bin/sqlite3 db1 {INSERT INTO geom1 VALUES(2, -10.0, -20.0, 200.123, -0.1234)}
exec /usr/bin/sqlite3 db1 {INSERT INTO geom1 VALUES(1, 0.0, 0.0, 20.1, 3.1415)}
exec /usr/bin/sqlite3 db1 {INSERT INTO geom1 VALUES(3, -100.0, -200.0, 300.0, 400.0)}

set x [exec /usr/bin/sqlite3 db1 {SELECT * from geom1 ORDER BY rect_id}]

puts $x

#exec /usr/bin/sqlite3 db1 close
[/INDENT]

---

