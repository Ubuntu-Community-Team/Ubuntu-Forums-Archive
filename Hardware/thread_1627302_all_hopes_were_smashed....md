---
title: "all hopes were smashed..."
date: 2010-11-21
forum: Hardware
---

### Post by Nesaskewatch on 2010-11-21
I have a laptop hard drive that was rendered unbootable when a cast iron pan fell on my Toshiba L500.  I have replaced the damaged drive with a new one months ago, but have found an urgent need to recover the data from the damaged drive.  I was able to boot the drive with a live dvd and could view *most* of it's content, but there are over two hundred gigs of apparently good data that I would like to recover and I am worried the drive will totally fail if I try and transfer everything using a thumb drive.  I'm thinking I need to yoink the data with as little stress on the damaged drive as possible.  So my question is; what would be the most gentle way to pull data from a mangled hard disk?  I have another laptop with more than enough space to accommodate the data.  I have a wireless router at home but am an idiot when it comes to networking.  I *could* acquire a USB transfer cable if that is the best way.  I also have an 8 gig thumb drive, but like I said, I am worried that is too stressful for the mangled drive?

Any help is greatly appreciated!  Apologies up front for possibly being slow to respond to suggestions.  It's snowing like the blazes here, and I will probably have to shovel some driveways for some elderly neighbours.  I will respond though!

Cheers in advance!

---

### Post by Joe of loath on 2010-11-21
Do you have a desktop to put the drive in? Your best bet is to put the drive in there with a 2.5" to 3.5" SATA adaptor, and assuming you have space, DD the whole drive to a file on a disk on the desktop. Then you can mount the file and recover all you need without having to access the disk again.

---

### Post by Sylslay on 2010-11-21
Well if You need just copy files use nautilus or midnight commander with care (copy by size) or 5min copy, 2 min break.

but I have no idea how and what kind of recovery tool You can use,
everyone has little diffrent menu,

PS. Just don't overheat smashed drive.

---

### Post by Jacdeb6009 on 2010-11-21
Hi there,

Just my two cents worth.

First, I would try to install the drive in a desktop, as suggested by Joe of Loath, that way you probably get the fastest data transfer rates and lowest temperatures.

Failing that, I would suggest an external docking unit (such as the Icy Dock MB881 or similar) where the drive is "exposed" and will naturally run cooler.  The main trick would be to keep the drive as cool as possible.

As for transferring the data, if you can actually mount the drive, the most efficient way is to use rsync.  Yes, it is commandline, yes you may need to learn how it works, but it is way quicker then most anything else and probably, under the circumstances, a lot "kinder" to your drive.

Copy in relatively smaller blocks of data, starting with the most important stuff first.

As for rsync, to get a good idea of how it works, set up two test directories on a good working drive and a couple of "dummy" files and just play around with it a bit to get a feel for it.  The man page is actually quite helpful.

Generally something like :

```
rsync -avz /source_device/source_folder/  /destination_device/destination folder
```Should do the trick.  Important to note the difference between the above and:

```
rsync -avz /source_device/source_folder  /destination_device/destination folder
```Also, be sure to select a directory far enough down the structure so that not too much data is copied at one time.  the rsync command as illustrated above will recursively copy the folder structure.

Hope you manage to get it sorted!

There is always the option to use a data recovery lab, but this gets expensive.  The last time we had this done on a 80Gbyte drive, it came to close to $1,000  !!

Cheers,

---

### Post by tgalati4 on 2010-11-21
I would put it in desktop machine with an adapter (as mentioned) and simply use the copy command.  Yea the drive will get hot, but it will be the quickest copy.

Get a new desktop drive to receive the contents.  Assuming the pan fried drive is sdb and the rescue drive is sdc:

sudo cp /dev/sdb /dev/sdc

Then do your recovery on sdc, basically deleting the stuff that you don't need, temporary files, duplicates, etc, then burn the important stuff to CD.

You will probably have errors on the rescue drive, so run a manual fsck on the drive:

sudo fsck -r /dev/sdc

Once you have corrected the errors the best you can, you can mount the drive and do some housecleaning.

If there are files that you were not able to recover, you still have the original drive to do some additional hacking with testdisk/photorec.

sudo apt-get install testdisk
man photorec

With all of this advice, we at least want to know the rest of the story.  Were you protecting your face from this frying pan that your wife threw at you?  Does a laptop make an effective shield against flying frypans?  What exactly did you say to her?

---

### Post by Nesaskewatch on 2010-11-22
> **tgalati4 said:**
> 
With all of this advice, we at least want to know the rest of the story.  Were you protecting your face from this frying pan that your wife threw at you?  Does a laptop make an effective shield against flying frypans?  What exactly did you say to her?

I was preparing the meal of the century and had the laptop open on the kitchen counter when a screw holding the pan rack decided to fail and caused a shower of pots and pans.  My head ended up being the shield as it deflected a much more serious strike!  The ministry of war and finance was quietly reading in the other room and swears she had nothing to do with it.  She did, however, fail a frying pan residue test performed immediately afterward...

Thanks for the suggestions!  I went straight out out looking for an adapter last night I discovered that my Toshiba has what is called an ESata/USB cable port for connecting hard drives!  Perhaps that will be much the same as adapting to my desktop?  I'll head down to the candy store later today and try and pick one up.  What a fluke!  I'd love to claim that I bought this Toshiba for that reason, but it was down to the rather more mundane reason that it was dirt cheap!  

I think I'm gonna try tgalati4's method.  I will practice doing it a bit, then try it in anger.  Looks like that will put the least amount of stress on the pan fried drive?

Cheers again for the good advice!  I'll report any results.

---

### Post by Nesaskewatch on 2010-11-22
I will also do the transfer on the front porch as the temp out there is -10 this morning!  Should help keep the drive cool.

---

### Post by Jacdeb6009 on 2010-11-22
Hi Nesaskawatch,

It's a good story, and I would stick to it :)

Hope you get is sorted, good luck!

Cheers,

---

