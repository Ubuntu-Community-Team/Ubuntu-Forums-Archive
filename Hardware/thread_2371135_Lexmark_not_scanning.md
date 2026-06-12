---
title: "Lexmark not scanning"
date: 2017-09-11
forum: Hardware
---

### Post by p33r on 2017-09-11
**Hi!**
have a 3-1 printer thats not wanna scan, either simple-scan or xsane finds it, 
but its found in xubuntu and i can print with it, only the scanner thing..
any ideas?  :-(

i have xubuntu  [COLOR=#333333][FONT=&quot]17.04, Zesty Zapus
my printer is a lexmark pro715 (wireless) [/FONT][/COLOR]

---

### Post by pdc on 2017-09-11
so that is a 2011 printer/scanner. To be able to use simple scan or xsane; then the backend SANE needs to know about the device; and sadly it is not listed in the list of known-about list of Lexmark devices [http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK](http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK)

_______

you could contact the guys who develop SANE: if you join the mailing list, [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel) then ask if they can help you: you have the hardware, they have the expertise ......... 

if you make progress, please let us know back at the forum, as it will help others

---

### Post by p33r on 2017-09-22
can i use something else then sane? :confused:

---

### Post by DAB4970 on 2017-09-22
is your OS 64 or 32bit?  If it's 64bit, I can copy the text from Brother Support that solved the issue with my Brother all-in-one.  There's 6 files that needed to be copied from one directory to another.  Does simple-scan or xsane find scanner?  If it doesn't, copying the six files could possibly be your answer, if this fits your case.

Another question:  how's the firmware on your printer?  Does it have the latest stable release installed?  I also see that 12.04 was the last Ubuntu release that is listed in Lexmark's OS compatibility list.

---

### Post by p33r on 2017-09-23
os is 64bit, either simple-scan or xsane finds printer, i could try it! the firmware is latest, weird... please post from brother!

---

### Post by DAB4970 on 2017-09-23
This is what the Brother site says, but I cannot guarantee that the software for Lexmark would be the same.  I have never used a Lexmark under Linux, in the past 7 years since I started using Ubuntu.

> 
[LIST]
[*][B]I'm using Ubuntu 11.10 or higher. I cannot scan from my Brother Machine.
[LIST=1]

[*]Install the scan driver.
[*]Copy the following files under /usr/lib64/ to /usr/lib/.


[B]For brscan Users:
/usr/lib64/libbrcolm.so.1.0.1
/usr/lib64/libbrscandec.so.1.0.0
/usr/lib64/sane/libsane-brother.so.1.0.7
/usr/lib64/sane/libsane-brother.so
/usr/lib64/sane/libsane-brother.so.1
/usr/lib64/libbrscandec.so.1
/usr/lib64/libbrcolm.so
/usr/lib64/libbrcolm.so.1
/usr/lib64/libbrscandec.so


[B]For brscan2 Users:
/usr/lib64/libbrscandec2.so.1.0.0
/usr/lib64/sane/libsane-brother2.so.1.0.7
/usr/lib64/sane/libsane-brother2.so.1
/usr/lib64/sane/libsane-brother2.so
/usr/lib64/libbrcolm2.so.1.0.1
/usr/lib64/libbrcolm2.so
/usr/lib64/libbrscandec2.so.1
/usr/lib64/libbrscandec2.so
/usr/lib64/libbrcolm2.so.1


[B]For brscan3 Users:
/usr/lib64/libbrscandec3.so.1.0.0
/usr/lib64/sane/libsane-brother3.so.1.0.7
/usr/lib64/sane/libsane-brother3.so.1
/usr/lib64/sane/libsane-brother3.so
/usr/lib64/libbrscandec3.so
/usr/lib64/libbrscandec3.so.1


[B]For brscan4 Users:
/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.1



[B]Example 
command(For brscan3 Users): 

[B]cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
[B]cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
[B]cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
[B]cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
[B]cp /usr/lib64/libbrscandec3.so /usr/lib
[B]cp /usr/lib64/libbrscandec3.so.1 /usr/lib

**[B][B][COLOR=#222222][FONT=Verdana][/FONT][/COLOR]**[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]
[*]**[B][B][B][B][B][B][B][B][B][B][B][B][B][COLOR=#222222][FONT=Verdana]&#8203;[/FONT][/COLOR]**[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]
[/LIST]
[/B]
[/LIST]

---

### Post by efflandt on 2017-09-23
Why to people mention Brother for a Lexmark? I have a Lexmark X205n all-in-one laser scanner/fax/printer. Lexmark's 64-bit Linux network scanner (sane) driver works in 64-bit 14.04 (regular system or virtualbox) and the 32-bit driver works in 16.04 in virtualbox. But the 64-bit version does not work in 64-bit 16.04 or 16.10 (so I imagine not in 17.04). Maybe that has something to do with changes to the way startup scripts work.

Printing works fine, because it does postscript (and HP PCL).

You would need to check on Lexmark website whether they have a Linux scanner driver. The most recent Linux network scanner drivers they list for your printer for Ubuntu are for 16.10 which might work. I don't know if this link will go right to them or if you need to select something from that page to get to the Ubuntu (Debian based) drivers.
[http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PRO715&focusedTab=DOWNLOADS#2](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PRO715&focusedTab=DOWNLOADS#2)

PS: I guess you need to select "Linux/Unix" from dropdown list and than "Ubuntu 16.10" (which is most recent they list). Try that and see if it works.

---

### Post by p33r on 2017-09-25
brother thing didnt work...[CENTER][COLOR=#000000]:|, no lexmark utilities or drivers did the trick, i will investigate this further to see if i can solve this! [/COLOR][/CENTER]

---

### Post by pdc on 2017-09-26
efflandt posted very good information; it would be well worth following that up; it would not be surprising if a few files from Brother left a lexmark device still slumbering.

---

