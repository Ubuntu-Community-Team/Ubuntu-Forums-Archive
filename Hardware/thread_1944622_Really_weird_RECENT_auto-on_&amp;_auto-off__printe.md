---
title: "Really weird RECENT auto-on &amp; auto-off  printer problem!"
date: 2012-03-21
forum: Hardware
---

### Post by WinRiddance on 2012-03-21
Boy, this is driving me nuts, especially since nothing on my system has changed ... except for standard updates with the update manager. My system is the same as before, no new or different hardware, and I'm using the same printer that I've been using for the past 8 - 12 months. The printer is a Brother MFC J410W, connected via USB 2.0 cable directly to my computer.

A few days ago, perhaps a week at most, I tried printing some forms that I print on a regular basis ... but this time nothing happened. The print job stayed in the cue for a long time ... BUT WITHOUT ANY ERROR MESSAGES.  So I checked ... SYSTEM ... PRINTING ... and saw that my installed printer had what appeared to be a **PAUSE BUTTON** on it ??? WTH ???

I right clicked for the printer properties where I saw the comment:
**Printer Unplugged or turned off**

Say what? How did that happen?
Of course when I checked everything, the printer power & cable were just fine.

Okay, so I figured this was just a quirk for some weird reason and restarted the computer. _After the restart my printer worked perfectly fine,_ didn't have to change anything anywhere. Selected my forms, chose print, and voila, both forms printed without a problem. **BUT** ... then today exactly the same thing happened. Same pause button, same "unplugged" message in the printer properties. Anyone else ever experience this or have a solution to this problem? I'd sure hate to restart my system all of the time before I print anything. This is really nuts ... !!!

.

---

### Post by WinRiddance on 2012-03-22
Okay, my **Brother MFC-J410W** Printer is working again!
Had to delete it from the system, followed by a new installation like this:
(same as when I first bought this printer since Ubuntu/Xubuntu will not recognize it automatically)

**1.** Go to the brother website, find and download these two files to your Desktop:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)
[FONT=Arial]mfcj410wlpr-1.1.1-1.i386.deb[/FONT]
[FONT=Arial]mfcj410wcupswrapper-1.1.1-1.i386.deb

**2.** Open your terminal in order to open your file manager with root privileges.
When the terminal is open, for NAUTILUS type: **gksu nautilus** (password required)
If you're using Xubuntu with Thunar file manager type: **gksu thunar**

**3. ** You have to follow step 2 because otherwise you may not have root access privileges for the following. Affter your file manager opened up, go to [COLOR=DarkRed]SYSTEM[/COLOR] ... then [COLOR=DarkRed]VAR[/COLOR] ... and finally open the [COLOR=DarkRed]SPOOL[/COLOR] folder. Once the spool folder is open, create a new directory/folder there, entitled: **lpd**
Now enter the lpd folder and create yet another directory/folder entitled: [/FONT][FONT=Arial]**mfcj410w**

Okay, that's all we need to do with the file manager. Back out of the folders and close your file manager. _Then we'll go back to the terminal_ for the final steps of the printer installation. First we need to enter the Desktop via the terminal. That's easy enough, just type:
**cd Desktop**

Since you downloaded those two files onto your Desktop, enter the following command in your terminal (wait for the process to finish once you've done that):[/FONT][FONT=Arial]

[/FONT][FONT=Arial]**sudo dpkg -i --force-all mfcj410wlpr-1.1.1-1.i386.deb**

If all went well without any errors, enter this command next:
[/FONT][FONT=Arial]**sudo dpkg -i --force-all mfcj410wcupswrapper-1.1.1-1.i386.deb**

Again, wait awhile for the process to complete. Exit the terminal by typing **exit.** When done, use your main menu to locate the printing options ... usually located in SYSTEM then SETTINGS, or something like that. When you locate the PRINTING options go ahead and click on that. _A small window with your printer should open up_ on your screen. If you see your printer, right click on it and then select SET AS DEFAULT from the menu. That's it, you're off and printing ....
(you might want to bookmark this forum link for future references)

.
[/FONT]

---

