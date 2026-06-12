---
title: "Dreamweaver MX 2004"
date: 2005-11-26
forum: General Help
---

### Post by speedy51 on 2005-11-26
I need to install Dreamweaver MX 2004 under Ubuntu. Could someone tell me an emulator that supports it?

---

### Post by Bachstelze on 2005-11-26
Wine doesnt. I haven't tested others. You may want to try Bluefish or Screem for HTML-editing under Linux.

---

### Post by tomwell on 2005-11-26
Perhaps Nvu is more what speedy needs, I mean Screem and Bluefish are only html code right??? If he needs wysiwyg then Nvu is better although perhaps Speedy knows Html code...

Peace

Tom

---

### Post by faizulzone on 2005-11-26
u shall try Crossover Office..
i've tried once and its work well

---

### Post by mhancoc7 on 2005-11-26
NVU is a nice WYSIWYG. You can also purchase [CrossOver Office]("http://www.codeweavers.com"). It runs DreamWeaver MX nicely in Ubuntu. I have it installed. You can check it out here: [http://www.codeweavers.com]("http://www.codeweavers.com")
Jereme

---

### Post by JurB on 2005-11-26
[QUOTE=mhancoc7]You can also purchase [CrossOver Office]("http://www.codeweavers.com"). It runs DreamWeaver MX nicely in Ubuntu. [/QUOTE]
 
not Mx 2004!  Use Nvu, it's good enough.

---

### Post by mhancoc7 on 2005-11-26
Oh yeah I missed the 2004 part. Nvu works great for me too.
Jereme

---

### Post by speedy51 on 2005-11-27
Thx to all guys.
Be patient with me, i'm new for linux world.

---

### Post by tomwell on 2005-11-27
LMAO!!! There have been 6 posts between speedy's first and last one, we have all decided what is best for speedy with out speedy himself...!!! LMAO!!!!

Speedy do you prefer a WYSIWYG html program or a program where you have to type in the code...?? 

Peace

Tom

---

### Post by kosmic on 2005-11-27
Hum just try wine and follow this guide from Frank's corner
 
[http://frankscorner.org/index.php?p=dreamweavermx]("http://frankscorner.org/index.php?p=dreamweavermx")
 
It is for dreamweaver MX
 
Then tell us if it worked for you

---

### Post by sixsixone on 2006-04-13
Speedy, if you're not prepared to put up with any linux substitutes, there are ways of getting Dreamweaver MX 2004 going in Ubuntu using Wine.

Face it, if you edit websites, you use dreamweaver, end of story. I did it by doing the following:

1) Install Crossover Office Standard, from [http://www.codeweavers.com/]("http://www.codeweavers.com/")
2)Copy my Macromedia directory from the My Programs folder on my Windows partition...
3)...to /home/cxoffice/support/templates/win2000/drive_c/Program Files
4)Google "Dreamweaver crack by FFF", and download the patch. The important files are the crack.exe and FILE_ID.DIZ. But I'd extract all the files to be safe; this method is unreliable enough as it is ;-)
5)Put the files in the Dreamweaver 8 folder of the win2000 template
6)Open up the Crossover Configuration tool and create a new win2000 bottle; call it something like dreamweaver or whatever. Close the configuration tool.
7)Use the "Run a Windows Command" tool in Crossover and choose the bottle you just created. Then open /Program Files/Macromedia/Dreamweaver 8/Crack.exe (i.e. the patch you just put into the folder). Click run. Leave the default settings in the patch dialogue and patch the dreamweaver. Click exit when done.
8)Use the Run command again and this time launch  /Program Files/Macromedia/Dreamweaver 8/Dreamweaver.exe (Dreamweaver MX!)

-------------------------------------------------------------
Dreamweaver should run!
-------------------------------------------------------------
I did this on Breezy on an Acer TravelMate laptop.
The obvious problem with this method is having to use a crack- I have a full version but the problem is a licensing service which wine can't emulate. While I resent having to crack a paid-for copy just to get it working, I guess you gotta be pragmatic sometimes...

Good luck, hope this helps!

---

