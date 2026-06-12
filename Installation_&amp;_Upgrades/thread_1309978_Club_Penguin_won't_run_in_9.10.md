---
title: "Club Penguin won't run in 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by wactuary on 2009-11-01
After upgrading to 9.10, everything seemed fine.  Everything except my 3 unhappy kids who can't get into Club Penguin ([www.clubpenguin.com](www.clubpenguin.com)) anymore.  I have flash 10 installed and Sun Java 1.6.0_16 set as my default java engine.  I'm running a 64-bit installation.  Other flash seems to work and I can do youtube and other java/flash website (nickjr.com) without problems.

What I'm getting is this:

The main site loads fine.  I click Play Now button.

New page loads and an embedded java applet loads and initializes.

Press the Start button and the button turns color like it was pressed, but nothing happens.

What should happen is it brings up a log-in page and the games begin.

I've searched and tried to the limits of my abilities.  I sure would appreciate any help from the community on this one!

---

### Post by wbm on 2009-11-01
> **wactuary said:**
> After upgrading to 9.10, everything seemed fine.  Everything except my 3 unhappy kids who can't get into Club Penguin ([www.clubpenguin.com]("http://www.clubpenguin.com")) anymore.  I have flash 10 installed and Sun Java 1.6.0_16 set as my default java engine.  I'm running a 64-bit installation.  Other flash seems to work and I can do youtube and other java/flash website (nickjr.com) without problems.

What I'm getting is this:

The main site loads fine.  I click Play Now button.

New page loads and an embedded java applet loads and initializes.

Press the Start button and the button turns color like it was pressed, but nothing happens.

What should happen is it brings up a log-in page and the games begin.

I've searched and tried to the limits of my abilities.  I sure would appreciate any help from the community on this one!


I also upgraded from 9.04 to 9.10 and Club Penguin works fine on my end. I had to install the restricted extras, which you probably did too if you can see YouTube videos.

---

### Post by wactuary on 2009-11-01
> **wbm said:**
> I also upgraded from 9.04 to 9.10 and Club Penguin works fine on my end. I had to install the restricted extras, which you probably did too if you can see YouTube videos.

Yup.  Restricted Extras are installed.

---

### Post by pjssilva on 2009-11-02
> **wactuary said:**
> After upgrading to 9.10, everything seemed fine.  Everything except my 3 unhappy kids who can't get into Club Penguin ([www.clubpenguin.com](www.clubpenguin.com)) anymore.  I have flash 10 installed and Sun Java 1.6.0_16 set as my default java engine.  I'm running a 64-bit installation.  Other flash seems to work and I can do youtube and other java/flash website (nickjr.com) without problems.

What I'm getting is this:

The main site loads fine.  I click Play Now button.

New page loads and an embedded java applet loads and initializes.

Press the Start button and the button turns color like it was pressed, but nothing happens.

What should happen is it brings up a log-in page and the games begin.

I've searched and tried to the limits of my abilities.  I sure would appreciate any help from the community on this one!

Are you using 64 bit. I am having the same problem in a 64 bit installation. It looks like it is a problem with the flash player in 64 bit (actually, if I am not wrong, Ubuntu uses the 32 bit version through some kind of bridge. I tried to install the 64 bit version of the flash player but I crashed the browser in Club Penguin).

The only way I could manage to walk around the problem was to install a 32 bit version of the browser. I copy the steps below. Please let me know if it works for you so we can think about the best way to report this bug. Note that if you install the 32 bit version of firefox below it will not have security updates from Canonical. However I think you can download the updates (probably being root) using the menu Help->Verify updates. I am not sure about this. In the worst case you will have to manually install the updated browser.

--- HOWTO install  a firefox 32 bit manually ---

Lines starting with a dollar sign must be entered in a terminal
(without the dollar sign):

0) Make sure you can run 32bit applications

$ sudo apt-get install ia32-libs

1) Get firefox 32 bit version in tar.bz2 format in from 
[http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

2) Move the downloaded file to /usr/local/lib32 (if the directory does
not exist, create it)

3) Unpack the file, for example

sudo tar jxvf firefox-3.5.4.tar.bz2

4) Move the created directory to firefox32 to make sure that you will
remember that this is the case:

mv firefox firefox32

4) Create a simple shell script with the contents below to call the 32bit version of firefox, name the file firefox32 and put it in /usr/local/bin:

--- Contents for the firefox32 script ---
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
linux32 /usr/local/lib32/firefox32/firefox -P 32bit "$@"
--- End of script ---

$ sudo chmod a+x /usr/local/firefox32

(Obs: note that the executable was called firefox32 and not firefox to
avoid conflict with the standard firefox. Note that I also made it
call the profifle 32bit on startup to avoid conflict with other
firefox profiles.)

5) Run firefox32 for the first time, it will open the profile manager:

$ firefox32

Ask it to create a new profile and name it "32bit". After that exit
the profile manager but make sure to either select your default
profile before exiting the manager or to uncheck the option "Don't ask
at startup", otherwise your default firefox (the 64bit version) will
start using the wrong profile.

Note that you will need to create such a profile for each user (in
this cases your kids).

6) Call firefox32 from the command line:

$ firefox32

It should start in the new profile (check, for example looking at the
bookmarks)

7) Go to club penguin and get the flash player using the "Get flash
player" link in the page. Select the .tar.gz version.

8 ) Unpack the downloaded .tar.gz somewhere, for example move it to /tmp
and unpack it there using

$ tar zxvf install_flash_player_10_linux.tar.gz 

9) Move the file libflashplayer.so to
/usr/local/lib32/firefox32/plugins

$ sudo mv libflashplayer.so /usr/local/lib32/firefox32/plugins/

10) Close firefox and start it again to see if it works. It should
work.

11) If it works, create a .desktop file to call it from the menu. For
example paste the following text in a file named
/usr/local/share/applications/firefox32.desktop

--- Contents for firefox32.desktop ---
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/usr/local/bin/firefox32
Icon=/usr/share/icons/gnome/scalable/apps/web-browser.svg
Terminal=false
Name=32 bit browser (firefox)
Comment=Alternate browser using 32 bit to access problem sites
Categories=Application;Network;
--- end of file ---

Now you should find an entry named "32 bit browser (firefox)" in the
menu and you can call your new browser from there.

12) For your kids you may want to create a shortcut for the new
browser in their desktop (just move the icon to the desktop from the
menu). It would be even nicer if you change the icon to a logo from
Club Penguin (just look for "club penguin logo" in goole) and the name
from "32 bit bowser (firefox 32)" to simply "Club Penguin".

---

### Post by wactuary on 2009-11-03
Thanks for that great post.  It's too late tonight, and I doubt I can do it tomorrow, but Wednesday I should be able to give this a test.  I'll report back with results.  (and yes.  I'm running 64-bit)

---

### Post by wactuary on 2009-11-04
I had more time than I thought (and spent more time than I should).  Here is what I have learned...

1)  the 64-bit Alpha release of Flash has no improvement.

2)  gnash isn't flash.  at least not yet, or not for this site.

3)  The posted solution of creating a 32-bit version of firefox does work.

(A typo in step 4, the chmod command should reference /usr/local/bin/firefox32)

I haven't finished playing with this and it's the first time playing with Profiles.  At least so far, it appears like you will be have to select Default for normal browsing and 32-bit when using the other version every time you start either instance of Firefox.  I'm not sure of the need for this yet.  Or if the 32-bit version desktop file can be adjusted to auto-select the 32-bit profile and leave the default profile to load unless otherwise specified?  Maybe it's just a command line switch that can be added to the different firefox icons?

Anyway, thanks so much for posting this solution.  In all my googling, I'd seen many threads on getting 32-bit flash to work in 64-bit firefox, but this is the first I'd seen of using a 32-bit instance of firefox.  At least until there is a more native solution, what are the downsides of using this instance of firefox all the time?



And of course, this is still a bug that I'd like to learn more about how to report and work toward fixing.  It worked fine in 9.4 (with 32-bit flash, I never tried 64-bit flash), what changed that it doesn't work with 9.10?  And why doesn't 64-bit work.  I know flash is not open source, so might not be anything that the Ubuntu community can control, but if I can help, please point me in the right direction.  Or if there is a way to work with gnash?  I have much more patience than my kids!

---

### Post by wactuary on 2009-11-04
Update:  Further research, the issue with the 32-bit flash in 64-bit Ubuntu 9.10 is documented in the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407")

There are multiple work arounds provided in the comments for the bug, the most compelling to me is the script in comment 143, further refined in comments 153/154.

The other interesting post is getting 64-bit flash alpha release to work.  For me, it just crashed firefox, so I didn't pursue it long.  But I stumbled upon [this]("http://blog.patshead.com/blog/2009/10/heavy-handed-fix-for-karmic-koala-64-bit-flash.html").  Some reports say by installing the package libadns1 the 64-bit crashes go away.  I'll test and report back.

---

### Post by Padsz on 2009-11-04
Try going on through miniclip instead or if u already do it from miniclip do in the main site instead.

---

### Post by beechmore on 2009-12-05
My Club Penguin stopped working after upgrading to 9.10. I tried most of the solutions mentioned in this thread to no avail.

I noticed that when clicking the Penguin Play Now button, Gnash was being used instead of Flash. I removed Gnash using the Synaptic Package Manager and hey presto, it started working.

To see if you have the same problem, right click on the play button and see if it mentions Flash. If it doesn't, then Gnash is probably being used instead of Flash.

Good luck.

---

### Post by phillw on 2009-12-05
Hi,

It's due to the flash part for FFox not putting itself in the correct area ..

Give me a couple of min & I'll dig the thread out. We cannot have people not allowed onto Club Penguin ---- Hungry Puffles :-(

Phill.

---

### Post by phillw on 2009-12-05
<< back

 				 				**Re: Flash Player Not Working in Firefox 3.5** 			
 			 			 		   		 		 		You need a little 'thinngie' for 64 bit .....

[http://ubuntuforums.org/showthread.php?t=1306113](http://ubuntuforums.org/showthread.php?t=1306113)

Do as [Amazona aestiva]("http://ubuntuforums.org/member.php?u=322041")  suggests.

It worked for another person who was doing much head scratching !!

Regards,

Phill.

---

