---
title: "Screen blanks instead of going off"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by kuukie on 2007-02-27
I've been using my nx6310 laptop quite happily for some time now and almost everything works (including the wireless bcm43xx/ndiswrapper drivers). One thing that really bugs me though is the power management.

What I'm trying to do: Completely switch the display off (that includes the backlight) instead of blanking it.

[i]What I have been doing: Switched to a console (Ctrl-Alt-F5) and logged in as root. Then everytime I wanted to switch the display off I'd go into the console and type: vbetool dpms off

Without the root shell it's even more stupid and frustrating when I want to switch the screen back on again: I have to type sudo vbetool dpms on, type in my password and pray that I get it right the first time. At least no stupid tool like gnome-screensaver would try to turn it back on again and blank it.[/i]

So I poked around the net for solutions and came across this:
chmod a+s /usr/sbin/vbetool #this gives normal users access to vbetool

Now I put vbetool dpms on/off into my ~/.fluxbox/keys file so I don't have to open a terminal and type all that to switch the display off/on

But when I gave my users this permission for vbetool and I started using the shortcuts it kept going into 'blank' mode after a few minutes again!

Somebody suggested to 'xset s off', which I did, but that didn't help, something still kept putting it into blank mode after a while

Please, please tell me what I'm missing here. Why does even something simple like switchnig off the display have to be such a royal PITA in Ubuntu? :( In Slackware stuff just worked with xscreensaver. But even that wouldn't work properly in Ubuntu.

---

### Post by kuukie on 2007-03-13
OMG, I am such a colossal dumbass ... forget all that was in the first post.

This is actually quite embarassing, because I've been using Slax for quite some time before getting Ubuntu on my laptop.

Here's the bleeding obvious solution:

Edit the /etc/sudoers file with # visudo and add the line kuukie ALL=/usr/sbin/vbetool

Argh ](*,)

---

