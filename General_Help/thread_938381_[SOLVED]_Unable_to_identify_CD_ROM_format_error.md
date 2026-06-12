---
title: "[SOLVED] Unable to identify CD ROM format error"
date: 2008-10-04
forum: General Help
---

### Post by bedhead75 on 2008-10-04
I'm trying to install a program into Wine that spans two CD's.  I have them as disk image files -- Disk1.iso and Disk2.iso.  I can use Gmount-iso to mount Disk1.iso to /media/cdrom0 and run setup.exe without any problem.  When I mount Disk2.iso to continue the installation, Gmount-iso gives me the "wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage" error.  Typing "dmesg |tail" into the terminal shows an "Unable to identify CD ROM format".  When I check the file type of Disk2.iso, by typing "file Disk2.iso",  I get "Disk2.iso: data".  Doing the same thing for Disk1.iso, which mounts fine, I get "ISO 9660 CD-ROM filesystem data UDF filesystem data".
     I read online somewhere that there might be a way to extract the data from Disk2.iso to a folder and repackage it as an iso in the proper format using the mkisofs command.  Does anyone know how to extract the data from the improper Disk2.iso file?  Thanks.

P.S.  Burning Disk2.iso to a CD using Brasero gives me a CD that isn't recognized  and can't be mounted when I put it in.

---

### Post by Sef on 2008-10-04
>  I have them as disk image files -- Disk1.iso and Disk2.iso. 

Is burning to DVD an option?

---

### Post by bedhead75 on 2008-10-05
Unfortunately burning them to DVD probably wouldn't help either.  I don't have a DVD burner.  Each iso file is just around 500mb anyways.  I need a solution that is strictly file manipulation on the hard disk.  Anyone have any suggestions??

---

### Post by tonybaqain on 2008-10-05
```

sudo apt-get install isomaster

```

hope to help you, have fun :)

---

### Post by hyper_ch on 2008-10-05
howabout catting them toget into one iso? No clue if that works:

```

cd /path/where/both/ISOs/are/
cat * > ~/combined.iso

```

---

### Post by bedhead75 on 2008-10-05
So after looking around for other software in addition to Gmount-iso, I installed Acetoneiso2 and it worked like a charm.  I didn't get to try using isomaster or the cat suggestion, but thanks for your help.  Apparently ubuntu has a hard time mounting certain iso files if they have been created in Windows XP or Vista.  This is something that needs to be fixed in future distros. People aren't going to be wanting to switch over to Ubuntu if files they backed up on CD or DVD from XP and Vista don't "just work"!

---

### Post by Claus7 on 2012-08-28
Hello,

facing exactly the same problem in maverick, I had to install from synaptic the **acetoneiso** package.

The installation went fine, I opened the program from Applications->Sound & Video -> AcetonISO

On the right had side there is the option mount, which I chose, yet the same iso image, which caused problems with the mount command from terminal, showed a new error:
  
> Error, could not mount image.

Solution:
Try converting the image to ISO or extract the content to a folder from the upper menu "Image Conversion."
NOTE: it is NOT possible to mount multi-sector images.
For more information, please visit official website: [http://www.acetoneteam.org](http://www.acetoneteam.org)

So, in order to avoid that, I chose the 'Image Conversion' tag which prompted me to install poweriso. I did so, and then I was able to see the contents of the iso file, by choosing to extract them to a folder. So, everything worked fine.

Thanks,
Regards!

---

