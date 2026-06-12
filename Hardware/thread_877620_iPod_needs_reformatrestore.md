---
title: "iPod needs reformat/restore"
date: 2008-08-02
forum: Hardware
---

### Post by Genius314 on 2008-08-02
Okay, so today I tried uploading some new songs to my iPod with Amarok. It said there was an error writing to the iPod, so I unmounted it an remounted it. This time, there was no songs listed under the "Devices" tab in Amarok, but the iPod was connected. So I decided to sync my collection with my iPod anyway.
Bad idea.
After that, my iPod (8GB nano) was twice as full as before (it says there's 1015MB free). However, I went to the music menu on the iPod, and it says "No Music." Amarok no longer sees any songs.

Trying to load the iPod in gtkpod gives me this error:
> Hashed file is 0 bytes long
Could not create hash value from itunesdb
Extended info will not be used.
iPod Database Import Failed: 'Illegal seek to offset 0 (length 4) in file '/media/IPOD/iPod_Control/iTunes/iTunesDB'.'

Newly mounted iPod at '/media/IPOD' could not be loaded into gtkpod.


So now I'd like to know if there's a way to fix this, or restore to factory default (without using Windows XP. I no longer have easy access to XP and iTunes. I *could* if I wanted, but I'd like to do this without Windows.)

Any help is appreciated. :)

Note: I had originally formatted the iPod in Windows so it was FAT32, and I was using Amarok to upload songs before. This is the first time that I've had any major problems.

---

### Post by Kaffiene on 2009-01-16
I am in the same boat, in fact...I was basically doing the same thing when Amarok (damn you!) ate my ipod. Let's hope for the best.

---

### Post by Rohan Kapoor on 2009-01-17
I don't believe that this is possible at all. Sorry!

---

### Post by vandorjw on 2009-01-18
It must be possible. All that Itunes does is download firmware and then extract it to the IPOD.
I am sure that it can be done manually if needed. 

Edit: Guess I am wrong. :s

---

### Post by Rohan Kapoor on 2009-01-18
> **cc7gir said:**
> It must be possible. All that Itunes does is download firmware and then extract it to the IPOD.
I am sure that it can be done manually if needed. 

Edit: Guess I am wrong. :s
Not manually you can't, you Itunes or Pwnage tool which jailbreakes to write firmware. Unfortuantely they only work on Mac or Windows. Sorry!

---

### Post by newegghead on 2009-03-26
I have a 160GB classic and i cant access it at all. iTunes won't mount it at all so i cant even restore it which is what it needs to work properly.  I have done everything i know it just wont re format, any ideas?

---

### Post by newegghead on 2009-03-26
never mind i found out how, you have to put it into disk mode to and then connect it, then you will be able to reformat with itunes 
PHEW!!!!

---

### Post by jdforsythe on 2009-09-11
This is actually very possible and very easy. Check out my how-to:
[http://ubuntuforums.org/showthread.php?t=1263715](http://ubuntuforums.org/showthread.php?t=1263715)

You do not need Mac or Windows, and you do not need iTunes.

---

### Post by networm1230 on 2009-09-11
hello everyone

I just formated my three hard drives. will here is what i used to format theme all.I used GParted  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)


Not!! you can use a live cd of ubuntu to format ipod or a hard drives.

how to!

1,run live cd 

2,go to system/Admin/than gparted it will look like a hard drive icon

warning not: be carefully not to format the wrong hard drive!

note: the live cd comes withe gparted but when us install Ubuntu gparted is not there.gparted dos not come with the install

---

