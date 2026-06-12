---
title: "Copying DVDs"
date: 2005-12-04
forum: General Help
---

### Post by Drunken Pirate on 2005-12-04
What is the best way to copy DVD's in linux? (This is for backup purposes only.)

---

### Post by manicka on 2005-12-04
I pefer [DVD shrink in Wine]("http://doc.gwos.org/index.php/DVD_Shrink_Breezy"), but there are native solutions as well. dvdbackup is a command line program that does a great job of just making a pure copy of the dvd. Excellent if you have a dual layer burner.

---

### Post by mcrosmar on 2005-12-04
[quote=Drunken Pirate]What is the best way to copy DVD's in linux? (This is for backup purposes only.)[/quote] 
I prefer DVDShrink too. I agree with manicka, about dvdbackup. A good program is xDVDShrink. But it doesn't support menus. You can only copy the main title.

---

### Post by Drunken Pirate on 2005-12-04
Ok, So I download DVDShrink, how should I burn it to a disk, and how should I decrypt it?

---

### Post by mcrosmar on 2005-12-05
[quote=Drunken Pirate]Ok, So I download DVDShrink, how should I burn it to a disk, and how should I decrypt it?[/quote] 
Have a look here [http://www.mrbass.org/linux/ubuntu/dvdshrink/]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")

---

### Post by manicka on 2005-12-05
[QUOTE=mcrosmar]Have a look here [http://www.mrbass.org/linux/ubuntu/dvdshrink/]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")[/QUOTE]

This how-to is for  hoary and will not work in breezy

---

### Post by mcrosmar on 2005-12-05
[quote=manicka]This how-to is for  hoary and will not work in breezy[/quote] 
Sorry manicka. You're right. :???:
I searched wiki and I found this: [https://wiki.ubuntu.com/dvdshrink]("https://wiki.ubuntu.com/dvdshrink")

---

### Post by remick182 on 2005-12-05
If you're mainly concerned with the movie itself, I would suggest lxdvdrip.  It takes a little longer to process the movies, but I've had a 100% success rate so far.  I found it after trying to get several of my movies to backup using DVDShrink and other Windows DVD programs.  DVDShrink only let me copy 1 movie flawlessly, a couple others gave me some serious problems and I had to keep going back and tweaking them to get them to work.  It was really annoying.
There's a complete Wiki for lxdvdrip [here]("https://wiki.ubuntu.com/lxdvdripOnBreezyHowto?highlight=%28lxdvdrip%29").

---

### Post by manicka on 2005-12-05
[QUOTE=mcrosmar]Sorry manicka. You're right. :???:
I searched wiki and I found this: [https://wiki.ubuntu.com/dvdshrink]("https://wiki.ubuntu.com/dvdshrink")[/QUOTE]


ah, I forgot about that page, shouldn't have....I wrote it :)

A more up to date version is here (but the server is temporarily down)

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

---

### Post by mcrosmar on 2005-12-05
[quote=manicka]ah, I forgot about that page, shouldn't have....I wrote it :)[/quote] 
..... :lol:

---

### Post by Drunken Pirate on 2005-12-06
[QUOTE=remick182]If you're mainly concerned with the movie itself, I would suggest lxdvdrip.  It takes a little longer to process the movies, but I've had a 100% success rate so far.  I found it after trying to get several of my movies to backup using DVDShrink and other Windows DVD programs.  DVDShrink only let me copy 1 movie flawlessly, a couple others gave me some serious problems and I had to keep going back and tweaking them to get them to work.  It was really annoying.
There's a complete Wiki for lxdvdrip [here]("https://wiki.ubuntu.com/lxdvdripOnBreezyHowto?highlight=%28lxdvdrip%29").[/QUOTE]


Im going to go after this one, because I would much rather choose a native method, even if it takes awhile. Thanks alot.

Whats the best method for burning the disk to a DVD?

---

### Post by remick182 on 2005-12-12
If you haven't already used lxdvdrip, you will find that you'll get prompted to insert a blank DVD after it compresses the movie files.  So you get the whole package with one program.:)

---

### Post by kpturvey on 2005-12-22
I'm having some problems with this myself so instead of creating a new thread I thought I would just add to this one. 

My daughter, two, has figured out how to put her own DVDs in the player without any assistance from me.  Although I'm quite proud of this feat, she hasn't yet learned how to hold a DVD without putting her fingers on the recording surface or treating it in such a way that ceases to perform as a DVD.  

So here I am trying to copy Shrek to a new disk.  The old one works fine in my computer but is essentially useless on the DVD player we have connected to the TV.  This is probably only the first of several of her shows that I'm going to backup and preserve somewhere that it will be safe from grape jam covered fingers.

So here we go...

I've got a dual layer recorder that connects to my laptop using USB.  The recorder works great with Verbatim dual layer disks (but not other brands.  I've asked BusLink for a firmware upgrade but they don't seem to know what their doing.  NEC has released the firmware upgrade some time ago, but only for internal drives.  I can record data to this drive without any problems.  It works great.  

I can also pull the data off the DVDs with dvdbackup and libdvdcss without any problems.  I have a perfect working copy of shrek on my hard drive now that I can play through totem-xine.  The menus work, everything works. 

Unfortunately when I burn it to DVD it doesn't work quite as expected.  The menus don't work perfectly.  There are long delays while it is loading.  On occassion the disk will freeze  at some scene.  

The command I'm using to burn the DVD is this:

sudo nice -n -10 growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video SHREK

There are two problems with this that I notice write away.

1) It would be better if I could do this in two steps so I could test the DVD by mounting the iso image.  I think I can do this with mkisofs, but I'm not sure if there are options other than the -dvd-video option.  Even if this works, I'm not sure that mounting the ISO will give me the same result as reading directly from the DVD.  My laptop is configured in such a way that I have to mount the DVD before playing it.  I don't think this is exactly equivalent to the way the DVD player connected to the T.V. works.  If anyone has a suggestion on how I can get totem-xine to play the DVD without mounting, in the same was as the DVD player downstairs does, I would greatly appreciate the information.

2) The second obvious error is that my DVDs are recoreded with all the files and directories having lowercase names.  This is an obvious difference between the original DVD and my copy.  I don't know if this matters, but it is certainly distressing that this obvious difference exists and that I can't seem to find a way to fix it.  The copy on the hard disk has correct filenames.

What I really want is an exact copy of the Shrek DVD I started with.  I don't really care if it is encrypted or not.  I would prefer that it wasn't, but an exact copy would be fine.  I understand that simply dd'ing the disk won't do.  Is there something similar that I can do to create an exact copy?

Any assistance would be greatly appreciated.

Thanks.

---

### Post by kpturvey on 2006-01-14
It seems the problem was with my DVD player.  It completely died today.   So, to recap, the commands necessary to duplicate a dual layer DVD on a dual layer drive are the following:

 dvdbackup -i /dev/dvd -M -o dir/

where /dev/dvd is the dvd device where the DVD to be copied is located and dir is the directory into which the data should be stored

To write all this data to the DVD+R DL we do the following:

 growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video LILOSTITCH_US/

Where /dev/dvdrw is the device of the dual layer DVD drive and LILOSTITCH_US/ is the directory created using the above command.

---

### Post by matva on 2006-01-14
guys, what about imgburn/dvddecrypter. Any luck in 5.10? I tried mrbass guide, but i didn't work.

Btw, kpturvey, is dvdbackup a program ? .... seems very easy.

---

### Post by manicka on 2006-01-16
[QUOTE=matva]
 is dvdbackup a program ? .... seems very easy.[/QUOTE]

yes and yes

---

### Post by qferret on 2006-01-17
[QUOTE=manicka]ah, I forgot about that page, shouldn't have....I wrote it :)
[/QUOTE]


LMAO!  That's funny  :razz: 

It'll be awhile before I forget the one I wrote. It's a good guide at what not to do LOL.

[http://www.ubuntuforums.org/showthread.php?t=118374](http://www.ubuntuforums.org/showthread.php?t=118374)

Seriously though ... drunken pirate ...check the thread & read the last post.  Easy as pie after all is sorted out.

---

### Post by handy on 2006-01-17
If all else fails...

Use Automatix to install Wine.

Use WineTools to configure it.

Then install DVDshrink, cause it's still the easiest to use, IMHO. :smile: 

Burn it one of the many ways.  I like NeroLINUX myself.

All the best...

---

### Post by MJSOnline on 2006-09-13
> **kpturvey said:**
> It seems the problem was with my DVD player.  It completely died today.   So, to recap, the commands necessary to duplicate a dual layer DVD on a dual layer drive are the following:

 dvdbackup -i /dev/dvd -M -o dir/

where /dev/dvd is the dvd device where the DVD to be copied is located and dir is the directory into which the data should be stored

To write all this data to the DVD+R DL we do the following:

 growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video LILOSTITCH_US/

Where /dev/dvdrw is the device of the dual layer DVD drive and LILOSTITCH_US/ is the directory created using the above command.

Hi.I did that at recviced this error message

[B]growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video /media/SD/DVDB
Executing 'mkisofs -dvd-video /media/SD/DVDB | builtin_dd of=/dev/dvdrw obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error[/B]

Any ideas how to fix this? Thanks. M

---

### Post by satbunny on 2006-09-20
> **mcrosmar said:**
> ..... :lol:

I have had some problems with installing lxdvdrip with Dapper. There are some dependency issues with streamanalyse and also I do not have tcmplex.

Has anyone got it working with Dapper?

UPDATE: I forced the install of streamanalyse, but then chose to use transcode and mplex when I edited the config file. I have also chosen to make an iso file with mkisofs rather than direct burn.

So, with those tweaks I used the wiki HOW-TO to get lxdvdrip to work on Dapper.

---

