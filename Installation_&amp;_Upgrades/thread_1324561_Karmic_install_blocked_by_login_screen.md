---
title: "Karmic install blocked by login screen"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by polarberg on 2009-11-12
Why is the first thing I get when I try to install Karmic a login screen where my old UN/PW doesn't work?

---

### Post by mac9416 on 2009-11-12
I've had this problem before. I was able to solve it by entering "ubuntu" as the username and leaving the password blank empty. However, I have suggested it to someone with this problem on Karmic, and it didn't work. So, there are no guarantees. ;)

Good luck!

---

### Post by polarberg on 2009-11-13
No dice. The console before the login screen is saying "unknown user: ubuntu," I assume that Ubuntu is trying to login with that name to start with. Logging in with my username, root, ubuntu or no username with no password, ubuntu or my password do not work.

What would really help is knowing why Ubuntu is sending up a login screen before I've even got a working system installed. If it's trying to piggyback on an old system...I mean, there's two things wrong with this, the first being that it never asked me to do so and the second being that I'm not trying to preserve any old Linux filesystem, but it would be nice to not have to reformat that partition because it's possible I still have personal files intact. If I don't get a satisfactory answer by tomorrow, I'm going to just reformat.

Edit: It also does this when I do "try Ubuntu without making any changes." Which is even more disturbing, because it suggests that the disc really *is* trying to piggyback on my old, broken system, making what ought to be a LiveCD not a LiveCD at all.

Editor's note: This has absolutely tanked my trust in Ubuntu straightaway. Nice, flashy installer, but I have no idea what to expect out of the installed system if I can't even get the installer to do - literally! - one thing right. Ubuntu's first priority should be repairing the damage they've done to themselves, however they've done it, in this latest release by altering the install procedure so as to effectively remove the user from the entire process.

---

### Post by mac9416 on 2009-11-13
Hey, polarberg,

Sorry you are still encountering this problem. I've read around for solutions, but there doesn't seem to be one clear fix. What I have found is that the problem appears to be erratic and occurs when GDM disables guest sessions (why, I don't know).

Here are my suggestions - mind you they only come from Googling around: first, I would try downloading the CD and burning it again at a very low speed to avoid curruption. If that doesn't seem to help, I would try making a live install on a USB drive using [Unetbootin]("http://unetbootin.sourceforge.net/"). That would avoid the corrupted CD issue entirely.

As I say, this has only happened to me once, and username "ubuntu" and a blank password worked for me. So, I can only hope the above suggestions help you out.

Good luck!

---

### Post by efflandt on 2009-11-13
Booting a live session from install CD normally just pauses at the login screen, then continues into gnome, auto logged in as ubuntu.  I have never seen it not continue, but maybe you have some hardware that is incompatible or requires proprietary driver (that needs to be enabled), or corrupted iso or burn.

Actually if install iso is on bootable USB using System, Administration, USB Startup Disk Creator from a working system (or working install CD) it does not even pause for any login.  If you boot it live from USB, it does a splash screen, then launches right into gnome as user ubuntu.  And even if you have persistent data enabled, set an ubuntu password, and as ubuntu or another user set gnome to "require" password login (not auto login), that radio button is cleared on the next boot and ubuntu still auto logs in (maybe root just su's to ubuntu).  For security reasons with persistent data I am trying to figure out how to "require" login during USB boot.

---

### Post by Silencedd on 2009-11-13
Hello,
I m new in this forum and i decided to try ubuntu for my 1st time. I had the same issue but i noticed in verbose mode that there is a device I/O error and was disabling my guest login. So i tried with another optical drive and everything went ok.
Hope this helps, u can try it with another CD also, maybe ur disk is damaged.

---

### Post by polarberg on 2009-11-14
Reburning worked. I did verify the disc the first time :\ Didn't encounter the login screen at all. God knows why.

---

