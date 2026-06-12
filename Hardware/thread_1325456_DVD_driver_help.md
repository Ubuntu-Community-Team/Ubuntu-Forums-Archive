---
title: "DVD driver help"
date: 2009-11-13
forum: Hardware
---

### Post by Amenotep on 2009-11-13
Hello, i'm running ubuntu on my laptop and it doesn't seem to recognize my dvd driver (it doesn't appear in places, but it does appear in disk utility).

I can start the live cd from it, and i shows up on bios. I can also open and close the tray, but when i put a disk in it, nothing happend (except the drive making the usual sound). If i restart with an audio cd on the drive when i log in again it recognizes the cd and i can play the audio etc, but if i take the cd out the drive disappears again.

If it's an empty cd nothing happens. I need some help with this, anyone?

---

### Post by delcypher on 2009-11-13
It sounds like everything is working fine, you're probably just not used to Ubuntu's behaviour.

In linux hard drives and DVD/CD drives need to be mounted. If a drive is not mounted it will not be accessible and it will not show up in "places" in Nautilus (GNOME file browser).

For example when you take your audio cd out, the disc drive disappears from the the "places" list - that is perfectly normal as your disc is no longer mounted. Although AudioCDs are actually an exception as they do not get mounted but Ubuntu will still display it in the places list.

Your cd/DVD drive should always be visable in "computer" though. Go to "Go > Computer" in Nautilus and it should be there regardless if anything is actually in the drive.

If you put a CD/DVD into the drive Ubuntu should automatically mount it for you. If not you can try going into "computer" and trying to browse the drive and then seeing if it mounts it for you.

If not then it's time to go to the command line.

Let me know how you get on.

---

### Post by Amenotep on 2009-11-13
Gosh i feel stupid... Yeah it seems to be working fine. However when i insert a blank disk, and i open a .iso file with Brasero, it asks me to insert a blank cd into the drive (even though one is already there). Any ideas?

---

### Post by Amenotep on 2009-11-13
no one?

---

