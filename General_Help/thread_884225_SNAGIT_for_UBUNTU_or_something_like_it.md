---
title: "SNAGIT for UBUNTU or something like it??"
date: 2008-08-08
forum: General Help
---

### Post by sandman3838 on 2008-08-08
Hello

I was curious about something....   :confused:

When I was using Windows there was a third party program that you added to your system called SNAGIT.  It wasn't a Firefox add-on or anything like that.  It was a separate program.  Basically all you had to do was hit your Print Screen Key on the keyboard and it would activate and let you shade and capture you current active program or window.

Basically it was a great way you grab only what you wanted from any web page without the that extra just they slap on there.

Please if you need more clarification checkout the Web sight. 

[http://www.techsmith.com/screen-capture.asp](http://www.techsmith.com/screen-capture.asp)

 Once you do and you get a better understanding of the program I have to ask this but has anyone come across anything remotely similar for Ubuntu or possibly as a Firefox add-on?

Thank you all for your help!  :)

---

### Post by mdsharp24 on 2008-08-08
Applications, Accessories, "Take a Screenshot" will take a screen shot of anything you have open. The command is:  gnome-screenshot --interactive

Also, in the repositories is gtk_recordmydesktop that will make a movie of everything you do in ogg format that you can then convert to AVI, MPG, WMV, etc... using ffmpeg

ffmpeg -i capture.ogg capture.avi

You have to install gtk_recordmydesktop and ffmpeg

M

---

### Post by thirddeep on 2008-08-08
I had a quick look at that application, and from the website, simple screen shot does not come close to what it can do.

Sounds like a fun project to do :-)

Thd.

---

### Post by mdsharp24 on 2008-08-08
Oh I'm sure the "Take a Screenshot" utility doesn't do everything this SNAGIT application can do, but until the OP tells his explicitly what he needs done my post should be sufficient.

---

### Post by sandman3838 on 2008-08-08
Close!
Snagit does do a lot more.
If you have a windows system hanging around check it out.

For now though, your suggestion will have to do.

Thank you for your help.:)

---

### Post by mb_webguy on 2008-08-09
Take a look at Xvidcap (which you can install by typing "sudo apt-get install xvidcap" in the terminal).  Xvidcap can capture both images and video from your screen in a variety of formats.  It also lets you select a specific area of the screen to capture, like you said SnagIt allows you to do.

If you just want to use it to capture images, you'll probably want to change some of the single-frame mode preferences, such as setting the Frames Per Second and Maximum Frames both to 1, and changing the filename, file format, and save location.  (Also, be sure to click Save Preferences when you're done, since otherwise the changes will only be in effect until you close the program.)

If you want to start Xvidcap with a keyboard shortcut, you can add one in Compiz.

---

### Post by todak on 2008-08-09
KSnapshot will also allow you to capture full 
screen, window under cursor, region or a section of a window.

---

### Post by crjackson on 2009-03-05
Have a look at [Shutter]("http://shutter-project.org/")

---

### Post by UbuntuNerd on 2009-03-05
> **crjackson said:**
> Have a look at [Shutter]("http://shutter-project.org/")

I second that I used it before it was Shutter, when it was "Gscrot" and its a very good tool it works in a similar way as the windows vista snipping tool.

---

### Post by tp42 on 2009-03-12
I use shutter since a few days and  I am happy with it, not only taking screenshots but also annotating them with text, arrows, pictures and censoring some portions of the screenshot etc). Besides that, the Shutter team is very helpful and open for suggestions!

---

### Post by r3delmasry on 2010-02-28
wow
searching give me grate result 
thanks gays for the Shutter 
its relay cool application 
thanks again

---

