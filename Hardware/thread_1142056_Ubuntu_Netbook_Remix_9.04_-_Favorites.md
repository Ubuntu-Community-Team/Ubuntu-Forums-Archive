---
title: "Ubuntu Netbook Remix 9.04 - Favorites"
date: 2009-04-28
forum: Hardware
---

### Post by ajaysutton on 2009-04-28
Greetings,

So this morning, I installed Remix 9.04 on my 1000HE.  I just dropped in a 250 gig SATA drive and formatted with Ext4, and I'm mostly pleased, but there's something I can't figure out.  

When I try to add applications to the "Favorites" category on the left, nothing happens.  I drag the icons there, but when I click on the Favorites, there's nothing in there.

I wondered if anyone else had seen anything similar.

Thanks much.

---

### Post by ajaysutton on 2009-04-30
It's hard for me to believe I'm the only one experiencing a problem like this, or at least that no one has any thoughts on it.  Perhaps I format and try again.

---

### Post by PhilMize on 2009-04-30
I'm gunna put it on my aspire one tomorrow when I'm free at work... I'll let you know if I have the same issue.

---

### Post by surfed on 2009-05-01
> **ajaysutton said:**
> Greetings,

So this morning, I installed Remix 9.04 on my 1000HE.  I just dropped in a 250 gig SATA drive and formatted with Ext4, and I'm mostly pleased, but there's something I can't figure out.  

When I try to add applications to the "Favorites" category on the left, nothing happens.  I drag the icons there, but when I click on the Favorites, there's nothing in there.

I wondered if anyone else had seen anything similar.

Thanks much.


The way to add them is by right clicking and selecting add to faves

---

### Post by ajaysutton on 2009-05-01
I appreciate that Phil, thanks very much.  I'm going to be out of town later today and tomorrow so I may not see your post till late Saturday evening but I'll be very curious to know how it works out for you.  Thanks again.

---

### Post by ajaysutton on 2009-05-01
Thanks for the reply surfed, I had tried that prior to trying to drag and drop them.  On one application, Adobe Reader, it put a star on the icon for the application but did not create a shortcut in the Favorites folder.

I don't know anything to speak of about Ubutnu's file system, but it almost seems to me like my user doesn't have permission to write to this folder or something.  

I'd seen on another web site that you could modify the things thar are in those categories using Alacart, same as you could using traditional menus, and I tried to change or move one icon or something, in Alacart, but did not see the change reflected in the UNR interface.  

I'm not sure what's up with that.  It's very confusing to a relative rookie.

I'm grateful for the input.  Thanks again.

---

### Post by wanconcepts on 2009-05-09
I have a similar issue where I can't seem to find where in the file structure to place links so they appear in the Favorites area.  The default favorites are not necessarily mine and I would like to add my own.  There was no place on the menu when right mouse clicking on a link in my 'desktop' that said 'send to favorites'  like was mentioned...Humm.  I too am using an eee 1000HE with a 250Gig drive with 2 Gig RAM and Ubuntu 9.04 netbook install.

---

### Post by ajaysutton on 2009-05-24
For the time being, I've gone back to straight 9.04.  I am using EXT4 and have found the speed improvement to be fantastic.  I might wait till 9.10 to try remix again on my 1000HE, I think.

---

### Post by relen on 2009-06-11
I installed UNR 9.04 yesterday and I'm having the same issue. In fact I think it's creating the link in the Other menu, and not in the Favorites menu. I currently have several icons in the appropriate app menu for the same app that I have been trying to put into Favorites using right-click+add.

This would appear to be because only root has write access to the file/directory and we aren't it. 

As you do not seem to be able to be root for real on an Ubuntu system (I say "seem" because this is my first experience of it), the only way I can think of of dealing with it is to chown the thing and make it writable by other users. Which can't be what you are intended to do.

Any suggestions anyone?

--Richard E

---

### Post by relen on 2009-06-12
I've documented further findings in this thread:
[http://ubuntuforums.org/showthread.php?p=7443503#post7443503](http://ubuntuforums.org/showthread.php?p=7443503#post7443503)

--R

---

