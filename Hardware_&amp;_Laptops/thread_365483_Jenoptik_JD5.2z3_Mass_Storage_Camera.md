---
title: "Jenoptik JD5.2z3 Mass Storage Camera"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by alyoung on 2007-02-19
I know for a fact this camera is a USB Mass Storage device, but it refuses to mount in Ubuntu, and any other Linux distro, for that matter.

Trying to mount /dev/sda1 gives an error of the device not existing, and mounting /dev/sda gives an error of can't read superblock'.

Any ideas?

The information in lsusb when the camera is connected is:

```
alyoung@alyoungbox:/media$ lsusb
Bus 002 Device 004: ID 0d96:5202 Skanhex Technology, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Thanks in advance.

---

### Post by Neobuntu on 2008-03-09
Yeah, What's up with this. XP sees my Panny fz18 as mass storage. Why not Kubuntu (7.10 updated)?

I can switch the camera to the printer transfer mode, then set up Digicam (Program) for that and get my pictures (Just like I had to do with the Olympus 550) but not movies, on the FZ-18. 

XP gets both pics and movies as mass storage. What the heck is going on? Is mass storage proprietary now?

Funny thing is, SDHC does NOT work on my XP, no matter the hot fix patches. Kubuntu works SDHC perfectly (in a specific SDHC reader). 

So why do new cameras not work as mass storage with (k)ubuntu Gusty?

I would think this should be priority. You know, the little things, like WORKING!

Also for others, that have the Panasonic DMC-FZ-18, the Windows software with it stinks. The "Silkypics"raw editor is useful but I find no (jpg) editing software (WTF) and/or broken program selections. Apparently, there's a problem with registering; as stated on Arcsofts site. See thier FAQ's BEFORE registration.

**Edit: But the "Impressions" app does a fine job retouching, red eye and more.**

Kubuntu is so much **less** BS. Why can't we get the camera mass storage working (again) too? It's all the camera manufacturers fault, right? (It may be.) Well, it worked on XP. So Kubuntu needs fixing or some dirty pool is going on with MS and/or Panny/Arcsoft. Open software rules. Get used to it. The sooner that propriety crap is put in it's place, the better. I guess OEM's will still be clueless, though. Who knows?

How about everyone with Ubuntu/Open software, email the manufactures of your stuff and make it clear that you want just as much compatibility and extras coming from them as Windows and Mac users do. Heck they could save a bundle on development if they'd simply sponsor open source apps for their hardware. I'd put their product first om my list. Wouldn't you? That way, if they dropped support, you'd still have on going community development on everything except the obscure (and most of the obscure too).

If I have to go slumming with XP to get the occasional movie (QuickTime, right from the cam, no less) digitally, it will be the only thing I do with XP. Ug! I wasted all night mucking with Windows, updates, firewall settings, DRM, registrations, installs (uninstalls and reinstalls again), and slower programs. yet, it's still a shame. A shame.

**UPDATE:** As I suggested, just use a USB reader but as I plugged in the cams USB cable, several times, I finally accessed the data; right from the Camera (card or internal). Therefore, since one can not put the cams internal memory in a separate USB/SD "reader", just keep trying (up to five times maybe). Obviously, this is for when your SD(HC) card gets full; you remove it and use your small amount of internal memory as a back up (or if your forget you SD card). Near as I can tell, the auto USB drive starter is getting confused, doing it twice and failing somehow to work, unless plugged in several times.

---

