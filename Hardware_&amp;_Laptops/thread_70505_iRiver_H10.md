---
title: "iRiver H10"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by paulfox on 2005-09-30
Hi all, has anyone got experience with this player with linux?
I insert it and it mounts as a regular device, and I can drag music to it. but the music doesn't show up in the list on the device - but it's definately there.

any ideas?

---

### Post by markr on 2005-11-04
I'm think of getting the H10 myself and was wondering if anyone has got it working properly with Ubuntu 5.10?

Mark.

---

### Post by sciurus on 2005-11-25
[http://easyh10.sourceforge.net](http://easyh10.sourceforge.net)

---

### Post by rbw42 on 2005-11-29
Hi Folks,

I have an iriver H10 and it works OK with linux. You can put music in there and listen to it using the "browser" function. (This is for a non-US model, in Australia. Apparently US models will not work with linux because they do not automount as a FAT disk.)

If you want to create playlists and stuff there is the "easyH10" thing mentioned above, but I tried using it and found it way too complicated to be worth the effort.

I've found my H10 to be annoyingly buggy and unreliable. I'd seriously recommend looking at something else if you're a linux-only user like me.

Cheers.

---

### Post by Travisty on 2005-12-09
I have been using My H10 with Ubuntu since the release of Breezy and have not had any problems. There is a program called easy H10 to help sync the the files on the H10. As **sciurus** pointed out, the program is located at sourceforge at [http://easyh10.sourceforge.net]("http://easyh10.sourceforge.net").

It is very simple to get Ubuntu to regognise your H10. Simply:
1. Turn of device.
2. Disconect battery and re-connect.
3. Connect cable to PC and H10.
4. Restart H10 while holding down both power button and the O button on the front. Hold until it says emergeny connect (3-4 seconds).

Ubuntu should now see and mount the drive.

Once you have easy H10 installed I found the PDF located **[here]("http://members.porchlight.ca/charm/download/iRiverH10-howto.pdf")** to be invaluable for setting the program up.

**paulfox**: did you run the sync command after you coppied your music over? If you didn't then you the H10 won't recognise the changes to it. Enter **easyh10 -Un -on /media/usbdisk** at the command line and see if that solves your problem.

---

### Post by Ibbelz on 2005-12-20
I use my iriver H10 in Ubuntu too. It works great with easyh10. Actually better then with Iriver plus in Windows. ;)

When the H10 is plugged to my computer Ubuntu automatically recognizes it, then I copy or delete mp3s and update the media database with easyh10. Just by typing *"easyh10 -U /media/H10"* in the shell, works like a charm. :)

---

### Post by keithjr on 2006-08-11
Are you guys using the US version of the H10?  It is a little different so the setup steps will change.  The US version does not have a removable battery, but has a small RESET button on top that you have to poke with a pin to get it to work.

Moreover, the hold-O-button trick is only needed for the US version since iRiver sold out to Microsoft and doesn't support universal-mass-storage unless the O button is held at startup.


I want to be sure about this before I go turning my player into a doorstop.  Has anybody had any success with the H10 **US version **and EasyH10?  If so, I will try it out.

---

### Post by wallacetheweasel on 2006-08-25
Yes, it works perfectly well with the US version.  In fact, I prefer it to using WMP in Windows.

---

### Post by BongoBob on 2006-08-27
Can someone walk me through setting up easyh10? I tried using [this]("http://easyh10.sourceforge.net/manual_cui.html"), but I got a ton of errors.

---

### Post by montgoja on 2006-12-12
I'll definitely have to take a look at easyH10.  Didn't know about that!
Anyone have any luck using the H10 with Amarok?  Ideally, I would like to use this program, as I already have all my music organized on it.  If anyone has gotten Amarok to synch with the H10, I'd love to know what I need to do.  Through the GUI of Amarok, it looks like it shouldn't be too hard, but I don't know what I need to do, and Amarok couldn't autodetect it.

Oh!  Forgot to mention, I installed RockBox on my H10, so that changes things around a bit, too, I guess.

---

