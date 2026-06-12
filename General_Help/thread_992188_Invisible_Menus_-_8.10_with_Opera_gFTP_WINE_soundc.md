---
title: "Invisible Menus - 8.10 with Opera gFTP WINE soundconverter"
date: 2008-11-24
forum: General Help
---

### Post by djringjr on 2008-11-24
Hello,

Does anyone have a fix for the "no visible pull down menu" problem with 8.10?

I notice this on the following programs:

Opera
gFTP
SoundConverter
WINE

Whatever is rendering those programs on the screen must be different than the majority of programs used in Umbuntu.

If you wish to see an easier variant of the problem, run gFTP.  With gFTP the problem happens in the program window itself, the drop down menus (when you click on "file" etc.) are fine.  Using gFTP, connect to a FTP server.  You will see icons but no text identifying what the icons mean.

If you select an UP or DOWN directory, and then return, you will see the text, but once you scroll down, the text will disappear.

Soundconverter and Opera both have pull down menus with invisible - not visible - text.  I have written to a friend who works for Opera about this.

My guess is that it is a GTK glitch, but then again, I'm usually wrong!

Does anyone have a fix for this?

Thanks 

David

Keywords:

---

### Post by mempman on 2008-11-24
i think it could be a problem with your compiz.  Try this:

go to run command box and do "metacity --replace"
then try restarting (or starting) the program that you have.  

If that doesn't work, you can try to start the assosiated program from command line, and then we you encounter the problem you can check what feedback you are getting in your terminal window.

---

### Post by djringjr on 2008-11-24
Hello and thanks.  I should have mentioned that I already tried that and it works but the command never resolves and the command line keeps on running.  BUT all the menus work - I think Opera still didn't work, but most of the other worked.

When I run gFTP from command line I get a complaint - most of these programs complain about the same thing.  
```

david@david-desktop:~$ metacity --replace
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
```  This command keeps running continuously - this is what out of the box Ubuntu 8.10 seems to do at least once installed on hard drive.

When I run gftp:

david@david-desktop:~$ gftp
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

As long as metacity --replace is running I have no problem with those two programs.  When this command continues to run, WINE shows text.  It's distorted but you can figure out what it must say.

I reinstalled 8.10 to get rid of this problem, but it is still here.

Best
David

---

### Post by aherbert01 on 2008-12-20
I had the same problem with wine and this fixed it:

[http://ubuntuforums.org/showthread.php?t=966709](http://ubuntuforums.org/showthread.php?t=966709)

> **DJ_Peng said:**
> Thanks to a [comment on the bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/144") by Peter Remmers I saw an [entry on the WINE FAQ]("http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf") that I missed somehow. I followed the instructions and I'm now 100% able to run WINE apps again.

For those who need a little more explicit instructions I edited my [blog post]("http://nancib.wordpress.com/2008/11/02/does-anyone-know-what-borked-wine-this-week/") to show how I resolved it.

Thanks to everyone who helped diagnose and resolve the issue.

---

