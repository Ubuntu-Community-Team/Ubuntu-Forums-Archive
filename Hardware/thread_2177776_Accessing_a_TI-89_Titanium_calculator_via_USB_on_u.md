---
title: "Accessing a TI-89 Titanium calculator via USB on ubuntu 12.04 LTS"
date: 2013-09-30
forum: Hardware
---

### Post by emrysm on 2013-09-30
I had some difficulty figuring out how to use my TI-89 Titanium on ubuntu, so I figured I'd put all the info I found into one place for others.

To access files on your TI-89t you will need tilp which can be installed via the repositories:[INDENT]$ sudo apt-get install tilp2[/INDENT]
 
This program allows you to access the files on the TI-89t, but it does not have any built-in capability for editing the files you get.  For that I found "Word Rider" :[INDENT][http://www.ticalc.org/archives/files/fileinfo/370/37007.html](http://www.ticalc.org/archives/files/fileinfo/370/37007.html)
[/INDENT]
 
The program is written for windows, but fortunately for us it was written in Java.  I was able to run it by[INDENT]1)  Right click (in Nautilus) on /wordrider-0.7/wordrider.jar and go to properties
[/INDENT]
[INDENT]
2)  Check (on the permissions tab) "Allow executing file as program."
[/INDENT]
[INDENT]
* I believe the above is the same as $ sudo chmod +x wordrider.jar, but I didn't try it that way.
[/INDENT]
 
Now, to run Word Rider you can do it 2 different ways:[INDENT]1)  Right click on it (in Nautilus), select "Open with..." and then "Java runtime 7" (it also works in Java runtime 6, but those are the only 2 I checked)
[/INDENT]
[INDENT]
2)  In a terminal run:
[/INDENT]
[INDENT=2]$ java -jar /**location_of**/wordrider.jar

Obviously with "**location_of**" replaced with the path to your wordrider.jar file.

[/INDENT]
 I have found that the program is fully functional when run this way.

[HR][/HR]
OK, so now that you have tilp and wordrider installed and working, here's how to get a file from the TI-89t, edit it, and put it back on your calc.

1)  Once the calc is plugged in, run tilp:[INDENT]$ sudo tilp --calc=ti89t 
[/INDENT]
[INDENT]
* You might have to plug/unplug your calc to get tilp to recognize it.
[/INDENT]
 
2)  Use the tilp GUI to get a file from the TI-89t[INDENT]a)  Get a fresh directory listing (which also verifies the program is working properly).[/INDENT]
 [INDENT]b)  You can drag files from the left (calculator) to the right (computer).  I made a folder in my home directory called ti89t so I had a place to keep these files.[/INDENT]
 
 3)  Once you have the files you want, close the gui (you might have to ctrl+c at the command line to end the process, I've had it hang multiple times) and unplug the calc (no reason to waste batteries while you type in WordRider).

4)  Now, run WordRider[INDENT]$ java -jar /**location_to**/wordrider.jar[/INDENT]
 
 5)  Edit files with WordRider[INDENT]Once this program is running you should easily be able to open, edit and save your TI-89t files.  I usually save them under a new name so I don't have any mishaps and lose all my work. 
[/INDENT]
 
6)  Once everything is saved, close WordRider and run tilp again:[INDENT]a)  Plug in TI-89t[/INDENT]
 [INDENT]b)  $ sudo tilp --calc=ti89t[/INDENT]
 [INDENT]c)  Get a directory listing on the left again to verify connectivity[/INDENT]
 [INDENT]d)  Locate the file you want on the right and drag it over to the left.[/INDENT]
 [INDENT]* It will appear that nothing happened, but your calculator should have small text at the bottom of the screen that says "RECEIVED" whatever file you sent.[/INDENT]
 
 
That's it.

I hope this helps someone who is trying to cram a lot of notes on a TI-89t, because that's what I used it for :D.  My winbloze version of TI Connect and WordRider failed miserably at doing this reliably, so I went to my Ubuntu machine and got a much more reliable system working.

---

### Post by judy2 on 2014-03-12
I just registered solely to thank you from the bottom of my heart. This really saved my butt this morning. I am new to Ubuntu and your instructions were so clear and easy. Thank you so much!

---

