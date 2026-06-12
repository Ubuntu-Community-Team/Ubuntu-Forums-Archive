---
title: "car maintenance record program?"
date: 2005-12-06
forum: General Help
---

### Post by Ryan483 on 2005-12-06
Long time lurker - First time poster here... Not sure if this is the right area for this, but anyway:

Does anyone know of a car maintenance record app for linux? This program 
would have oil changes, repairs, mileage, etc. There are many, many applications out there for windows that do this - but I don't want to use XP:)
And it would help me out a lot since I own several automobiles.
Thanks!

---

### Post by teaker1s on 2005-12-06
your best bet would be to try to run a windows prog with 'wine' unless anyone has more ideas

---

### Post by Ryan483 on 2005-12-06
Well right now I am just using a spreadsheet since I have not found a program I really like yet. I will keep looking and report back if I find anything.

---

### Post by Tony3286 on 2007-09-09
Hay Ryan,
I've been using Ubuntu for 1 month now and have found MOST of the programs I used on Windows XP with similar Linux versions - BUT NOT a Car Maintenance program. I know its been almost 2 years from your original post, but I was interested to know if you ever found a car maintenance program that would work? I'm a fanatic with my cars and want a program that I can document my automobile maintenance and repairs.

Tony

---

### Post by Ryan483 on 2007-09-09
Nope, never found anything.

---

### Post by Tony3286 on 2007-09-10
Ryan,

Found one called Car companion- check it out  at:
[http://www.chocolatay.com/rails/car_companion/](http://www.chocolatay.com/rails/car_companion/)
also found it on Sourceforge.net.

Problem is, I'm not that familiar with installing  Linux programs. This file comes compressed using .tar.gz.
I was able to uncompress it in Ubuntu but now what?

---

### Post by Ryan483 on 2007-09-10
Tony,

Nice find. I'm in the middle of coding a  c++ project due by midnight for school, otherwise I would reply with instructions for you. Do you have Java installed on your machine? If so, You should be able to execute the jar file.

---

### Post by langster on 2007-09-10
An Automobile Maintainance program? Jolly good. I am salivating over a silver 350 Z and desire such a program. Please post a screen shot if you get it working for you!:popcorn:

---

### Post by Tony3286 on 2007-09-10
Ryan,
I'm almost positive Ubuntu has Java installed. I went through the files that were unpacked, but could not find a .jar file - plenty of Java files though. Like I had previously said - I'm VERY VERY new to Linux - When you have some free time, I'd appreciate a helping hand to install Car companion in Ubuntu feisty.

Tony

---

### Post by coggins on 2007-09-10
> **Tony3286 said:**
> Ryan,

Found one called Car companion- check it out  at:
[http://www.chocolatay.com/rails/car_companion/](http://www.chocolatay.com/rails/car_companion/)
also found it on Sourceforge.net.

Problem is, I'm not that familiar with installing  Linux programs. This file comes compressed using .tar.gz.
I was able to uncompress it in Ubuntu but now what?

Open the folder created when you extracted the archive.
Double-click "CarCompanion" (the one with no extension).
Ubuntu will give you some options of how to open it, choose "Run".

If it doesn't work you may need to install the java runtime environment.  
You could check whether you have it by typing java -version in the terminal.
Use synaptic to search for "jre" and install the Sun Java Runtime Environment v6 or similar.  

Sorry if that isn't too precise, I already had the dependencies so it was automagic for me.

---

### Post by coggins on 2007-09-10
> **Tony3286 said:**
> Ryan,
I'm almost positive Ubuntu has Java installed. I went through the files that were unpacked, but could not find a .jar file - plenty of Java files though. Like I had previously said - I'm VERY VERY new to Linux - When you have some free time, I'd appreciate a helping hand to install Car companion in Ubuntu feisty.

Tony

You got in while I was typing!

CarCompanion.jar should be in the folder called CarCompanion, i.e. the top level of what you extracted, and the one that contains the folders "help" and "lib".  If you don't see these, either the download was corrupt or you may not have extracted the whole archive

---

### Post by Tony3286 on 2007-09-10
Fantastic! Thats what I needed ! I installed java 6 , clicked on the Icon and boom - program came up after clicking RUN!

Thanks sooooooo Much
Tony

---

### Post by coggins on 2007-09-10
Glad to be of service

---

### Post by Tony3286 on 2007-09-10
Thats what I needed - Java 6! One last question -
How can I move that icon, that executes the program onto my main desktop and be able to execute it from there?
I had created a link and copied it to my desktop, but the only Icon that executes the program is the Carcompanion icon in the directory I had made called  "Car"

---

### Post by coggins on 2007-09-11
> **Tony3286 said:**
> Thats what I needed - Java 6! One last question -
How can I move that icon, that executes the program onto my main desktop and be able to execute it from there?
I had created a link and copied it to my desktop, but the only Icon that executes the program is the Carcompanion icon in the directory I had made called  "Car"

Right-click the desktop and select Create Launcher...
Type: Application
Name: whatever you like
Command: click browse to find the file you use to start Car Companion <<NO!
in that same folder is a file called "CarCompanion.jar" select it instead.
Now edit the Command: entry by adding java -jar to the beginning.
click OK.

---

### Post by Tony3286 on 2007-09-11
Can't thank you enough!  I spent at least an hour (before I read your post) playing with the Launcher on the desktop. The key was "Java-jar" Couldn't understand why its not launching - still in Windows Mentality!  

If I found out one thing, its that "EVERYONE" in any of these forums are so helpful and PATIENT.
Thank you so much again - little by little , I'm learning.

Tony   :)

---

### Post by notwen on 2007-09-11
> **langster said:**
> An Automobile Maintainance program? Jolly good. I am salivating over a silver 350 Z and desire such a program. Please post a screen shot if you get it working for you!:popcorn:

Here's a [link]("http://sourceforge.net/project/screenshots.php?group_id=84810&ssid=11864") to the Linux screenshot on the source forge site.  Looks tempting, I may give it a try once I get home.

---

### Post by Tony3286 on 2007-09-12
Well got the Car Companion up and running - added all my maintenance dates etc, even put a photo of my car - THEN - looked at the reports - everything looks fine - go to PRINT and BOOM - nothing!
Saved the file on the desktop and realized the extension is .ps POSTSCRIPT !! Now have to see how to print this extension on Ubuntu - Maybe Ghostscript? Anybody have experience with Ghostscript and Ubuntu or a similar program?

---

### Post by coggins on 2007-09-13
I don't have a printer at this location, so I can't investigate the underlying problem, but I can perhaps give you a pointer on the postscript thing, if you haven't figured it out already.  You should be able to open the .ps with evince (aka Document Viewer), which I believe installs with ubuntu - I don't remember having to install it...  From there printing should be trivial, assuming your printer is set up and working.  Of course printing is rarely as easy and reliable as it should be (on any operating system I've used), so YMMV.

---

### Post by Tony3286 on 2007-09-14
I gotta give Evince a try! I'm at work ,so tonight , thats my project!  My Brother printer is up and running after a few days of hunting on the Ubuntu forum for help with my MFC 210C Brother install.

Just went to the Evince site , it states -  Supported Document Formats  "Postscript using the GhostScript backend" Does that mean I still have to install Ghostscript (GSview) for Evince to read Postscript?

Thanks again!

---

### Post by coggins on 2007-09-14
It turns out that printing is seriously broken in Java 6.  There are some workarounds talked about - see [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/86970]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/86970")  - but they're pretty complicated and I couldn't make them work without breaking other things.  So I'm going to make you install java from the repos again! sorry... This time select sun-java5-jre to get the previous java version.  After it has installed, go to the command line and type ```
sudo update-alternatives --config java
``` and select the number corresponding to java-1.5.0.  Now open and run Car Companion as before, and printing should be fine.  If at some point you need to use Java 6 for something, run update-alternatives again to change it back.

---

### Post by Tony3286 on 2007-09-15
[SIZE="3"]YOU are the MAN![/SIZE]  
Did exactly what you said and I'm up and printing!

Please don't apologize about reverting back to Java 5!!  You have been a **tremendous** help with getting this particular program up and running  **AND** teaching me more about Linux. I truly believe its people such as yourself who help us all in this forum , that have made Ubuntu the success it is.

Thank you once again for ALL your patience!

Tony

---

### Post by Tony3286 on 2008-03-17
Found another Car Maintenance program - called Vehicle Maintenance Tracker - VMT at
[http://vmt.sourceforge.net/](http://vmt.sourceforge.net/)  - Java based - more user friendly - only problem - as of yet , no way to print reports such as Maintenance History - but allows you to add routine maintenance (a lot already listed)  and many other features. Even your automobile picture can be added - Worth a try !

---

