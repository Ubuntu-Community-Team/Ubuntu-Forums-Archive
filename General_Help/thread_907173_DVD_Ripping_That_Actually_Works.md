---
title: "DVD Ripping That Actually Works?"
date: 2008-09-01
forum: General Help
---

### Post by lightnb on 2008-09-01
I'm running Ubuntu 8.04, and I've tried a TON of different programs and tutorials, and none of them seem to be able to rip a DVD to an .ISO file, without halting on one error or another.

I'm trying to make an archive copy of my commercial DVD's, so they are most likely encrypted, and some are dual-layer. Does anyone know of or use a program that actually does the job?

Thanks!

---

### Post by sloggerkhan on 2008-09-01
well, offhand, I'd start with not trying to rip to ISO.

Rather, you should be looking to get the data, then burning that data sized to an appropriate fit for the disk, in a format that can be read by the player you choose.

It's I'd look into DeVeDe or Dvd95 for what you're trying to do, though you could do it with most ripper/encoders. Key to realize that DVDs are nothing more than properly named mpeg-2 files with some added files for menus and such.

---

### Post by lightnb on 2008-09-01
I was thinking ISO, since it's a single file that burns to an exact clone of the original disk. If I take the data as separate files, will all the feature and menus work again on the new disk?

---

### Post by tuskenraider on 2008-09-01
> **lightnb said:**
> I'm running Ubuntu 8.04, and I've tried a TON of different programs and tutorials, and none of them seem to be able to rip a DVD to an .ISO file, without halting on one error or another.
I'm trying to make an archive copy of my commercial DVD's, so they are most likely encrypted, and some are dual-layer. Does anyone know of or use a program that actually does the job?
Thanks!

wine + dvddecrypter and dvd shrink work pretty well... sadly its the anydvd that keeps me sorta tied to windoze. gosh darn you slysoft.. make anydvd work in wine or a linux equal!!!!!!:confused:  

tusken

---

### Post by sloggerkhan on 2008-09-01
> **lightnb said:**
> I was thinking ISO, since it's a single file that burns to an exact clone of the original disk. If I take the data as separate files, will all the feature and menus work again on the new disk?

Yes, so long as the video's decrypted and you include the proper files.

It used to be that you couldn't exact clone DVds because they wouldn't fit. It might be possible to have some sort of success with imaging, but I've never tried doing things that way at all.

---

### Post by bigbrovar on 2008-09-01
u dont really need any fancy 3rd party application to rip a dvd on ubuntu .. insect the dvd in ur computer .. right click on the dvd icon on your desktop .. choose **copy disk** and **copy disk to file image** then click **write** .. it would ask where u want to save the file .. and it should start .. or better still  open terminal applications/accessories/terminal and run this ```
sudo dd if=/dev/cdrom of=/dvd.iso
```
when do the image would be saved in your home directory

---

### Post by rbmorse on 2008-09-01
Bigbrovar: Does dd work with encrypted DVDs?

---

### Post by Bachstelze on 2008-09-01
> **rbmorse said:**
> Bigbrovar: Does dd work with encrypted DVDs?

No, dd will just blindly copy the DVD. To decrypt it, you can use e.g. mplayer (which will give you decrypted VOBs) :

```
mplayer dvd://1 -dumpstream -dumpfile title1.vob

```

---

### Post by mb_webguy on 2008-09-01
> **HymnToLife said:**
> No, dd will just blindly copy the DVD. To decrypt it, you can use e.g. mplayer (which will give you decrypted VOBs) :

```
mplayer dvd://1 -dumpstream -dumpfile title1.vob

```

Translation:  Yes, dd will blindly copy any DVD, even if it's encrypted.  If you want to have decrypted VOBs instead, you can use mplayer.

---

### Post by todak on 2008-09-01
I am rather successful using **libdvdcss2** and **k9copy**. On the rare occasions that I get an error during the copy process, it is due to a physical defect on the original disc itself (not always visible to the eye), which will render it unplayable anyway.

---

### Post by iheartubuntu on 2008-10-23
> **todak said:**
> I am rather successful using **libdvdcss2** and **k9copy**. On the rare occasions that I get an error during the copy process, it is due to a physical defect on the original disc itself (not always visible to the eye), which will render it unplayable anyway.

I too have always used K9Copy. But since Ive upgraded to Intrepid Ibex, its not working for me anymore. K3B works GREAT for copying a dvd to the desktop and making it an ISO, but on DVDs bigger than 4.4GB, I dont know how to shrink them. DVD95 works pretty good most of the time to shrink the ISO, but on some discs Ive found it wont work.

---

### Post by andrew.46 on 2008-10-24
Hi,

There is a commandline method. Using vobcopy with libdvdread + libdvdcss this syntax copies the dvd (called 'Batman' in this example) to your disk:

```
$ vobcopy -m
```

Then run:

```
$ cd Batman
$ mkisofs -v -dvd-video -o ../Batman.iso .
```

and navigate out and burn the iso:

```
$ cd ..
$ growisofs -dvd-compat -Z /dev/dvd=Batman.iso
```

Works well for me with dual layer blanks.

  Andrew

---

