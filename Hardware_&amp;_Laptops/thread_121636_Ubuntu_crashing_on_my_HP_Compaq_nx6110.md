---
title: "Ubuntu crashing on my HP Compaq nx6110"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by hugovdm on 2006-01-25
After a certain amount of use (ranging from a few days, to a few hours), my machine crashes. It happens "gradually", windows stop repainting, can't open new apps, can't close a Gnome terminal tab, switching to text mode gives me just a blank screen with a blinking cursor, and no way to switch back. I believe I've heard an MP3 finish playing, possibly even more than a minute left, while the next one couldn't start. Recently had a flac stop in mid-song though.

I've a strong suspicion/hunch it's related to the hard-drive or IDE interface. That's why I don't get any info in the logs. Apps seem to continue working until requiring the hard drive (next mp3... gnome terminal closing requires writing bash history, etc), and I've also seen the odd ide log message about hdb...:

Jan 24 23:07:24 localhost kernel: [4295181.598000] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
Jan 24 23:07:24 localhost kernel: [4295181.598000] hdb: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jan 24 23:07:24 localhost kernel: [4295181.598000] ide: failed opcode was: unknown

(This was what inspired my hunch/suspicions, even if it is unrelated.) I've not seen this about hda though.

Is there any way this is related to software? I really think this must be a hardware issue, and the laptop is less than 2 months old, well within the warranty. It didn't come with Linux preinstalled (South Africa), so I've wondered if I'd be required to reproduce similar crashes in Windows before sending it back. That wouldn't be acceptable to me though, if this is a hardware issue. I'm therefore just fishing for some knowledgable person to agree "send it back", then I will do so. Guess I need to dig up the contact details of HP support in South Africa. Will ask the people that sold it to me.

Thanks!
Hugo van der Merwe

---

### Post by stream303 on 2006-01-25
My old Dell Optiplex GX150 would hard reboot randomly until I changed the color depth in xorg.conf down from 24 to 16 bits.

Video issues maybe locking up the works?  Just a stab in the dark...

---

### Post by jml on 2006-01-25
I agree with stream303. you problemsounds like your computer is using up resources as it runs and the most resource hungry appliction you are running is thevideo.

Since you bought the laptop with windows, the vender may not authorize a return if you are having problems with an "unsupported" operating system.  If changing the video settings dosen't work, you may want to try to reproduce the problem in Windows. If it still happens, then you probably have a hardware problem and you should be able to return it under warranty.  You would probably have to reinstall Windows before the vendor would accept the laptop in return anyway.  

The HP NX series laptops have a reputation for being rather Linux friendly.  For a brief time, HP even offered an NX series laptop for sale that was loaded with 
SUSE Linux.  Good luck,and let us know what happens.

Joe

---

### Post by mips on 2006-01-26
Hugo,

I also have a nx6110 that performs flawlessly, Kubuntu 5.10.

Try turning DMA on/off for that drive and see what happens but either way it should not do what it is doing.
Your drive might be on it's way out...

1. I would suggest you backup your data asap.
2. I suspect you have a Seagate HD as that is what HP seems to favour and they are crap. You can verify this via your system or physically by removing the drive. Use Seatools Desktop to check your drive, [http://www.seagate.com/support/seatools/](http://www.seagate.com/support/seatools/)  If it is not a seagate drive try the manufacturers website as they all have tools.
3. Reinstall (K)Ubuntu and see if it still happens.
4. Use the system restore CD to restore your laptop to its Windows state and ship back to Vendor or HP.

[http://welcome.hp.com/country/za/en/contact_us.html](http://welcome.hp.com/country/za/en/contact_us.html)
HP services and support tel: 0860 001 030

---

