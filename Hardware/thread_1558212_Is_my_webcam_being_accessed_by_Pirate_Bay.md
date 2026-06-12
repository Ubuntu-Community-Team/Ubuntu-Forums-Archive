---
title: "Is my webcam being accessed by Pirate Bay?"
date: 2010-08-21
forum: Hardware
---

### Post by dolphinsonar on 2010-08-21
Hi folks,

While searching on piratebay.org, a window popped up and accessed my webcam.  This really freaked me out.  I use adblock and firefox, so I thought I was safe from this type of thing.  The window that popped up was from livejasmin.com and started showing porn on my screen while advertising for a webcam chat.  This isn't something that I requested, it just popped up and started showing me porn while I was using piratebay.

I know that my webcam was accessed because the blue light next to the lens of my cam flashed on momentarily.  Does this mean that a porn site now has a snapshot of me?  I suspect this has something to do with Flash settings, but I don't know how to permanently stop Flash from accessing my camera or microphone.  The way it is now I think you can only disable access on a per session basis.

Anyone else experience this?

---

### Post by tazz19790 on 2010-08-23
mine does this too i i noticed it when i when to a blog that has streaming for the owner but also you can cam chat with my integrated webcam light flashed once and it does this every now and then i dont know if it is because of sites that have cam chatting or if someone has access to my computer remotely and is taking pictures if anyone figures it out that would be nice but i think it might be websites that have cam chat also i have cheese so if you have it it might be cheese doing something

---

### Post by Fafler on 2010-08-23
A quick fix from the top of my head:

sudo chmod 000 /dev/video0 

Assuming the device name is actually /dev/video0. You'll have to do this after each reboot. And of course there should be a better solution than this.

---

### Post by IcarusR on 2010-08-25
In Firefox you can install YesScript addon, this allows you to select sites to block javascripts popups.

Details here

[https://addons.mozilla.org/en-US/firefox/addon/4922/]("https://addons.mozilla.org/en-US/firefox/addon/4922/")

---

