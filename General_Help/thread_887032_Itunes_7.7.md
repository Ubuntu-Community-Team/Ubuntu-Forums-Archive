---
title: "Itunes 7.7"
date: 2008-08-11
forum: General Help
---

### Post by stevecov on 2008-08-11
Hey guys,

I need to get Itunes 7.7 on my ubuntu so I can use my Ipod without logging onto windows vista so i need it to recognise the Ipod touch. I need 7.7 to use the applications feature, is this possible? All help is much appreciated, thanks!

---

### Post by aysiu on 2008-08-11
> **stevecov said:**
> Hey guys,

I need to get Itunes 7.7 on my ubuntu so I can use my Ipod without logging onto windows vista so i need it to recognise the Ipod touch. I need 7.7 to use the applications feature, is this possible? All help is much appreciated, thanks!
From [the Wine iTunes 7.7 page](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12953&iTestingId=28790): > **What works**
Audio Playing Functions

Importing CDs (shows up as a device and not a CD though)


**What does not**
iTunes Store lags, it works but it works slowly

iTunes does not recognize my CD drive as a CDR, but instead as a device. An error saying the registry settings are incorrect comes up on boot.


**What was not tested**
Burning CDs/MP3 CDs (iTunes did not recognize my CD drive)


**Additional Comments**
In order to prevent flickering screen you need to set QuickTime to use the Safe Mode (GDI only). This requires GDI libs to be installed.  Now I've never been able to successfully install iTunes myself with Wine. I believe it's more complicated than just double-clicking the .exe file (even with Wine installed). You may want to look around for a guide.

You're probably better off trying to find a way to get your iPod Touch working with a native Linux program (AmaroK, Banshee, GTKPod, Rhythmbox).

This page may help you:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by Mgiacchetti on 2008-08-11
you dont really need itunes

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

this one has many alternatives
[http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/](http://www.simplehelp.net/2007/07/08/10-alternatives-to-itunes-for-managing-your-ipod/)

in windows you will find that winamp has ipod compatibility as well.

---

### Post by damis648 on 2008-08-11
The most up-to-date version of iTunes work almost flawlessly with Wine, except np iPod syncing.:( See this page for syncing music using some native Ubuntu application like Rhythmbox: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) ,although there will be no app support.

---

### Post by azuresong on 2008-08-12
With [Aniosoft iTunes Backup](http://www.aniosoft.com), yuo can easily backup/restore your iTunes library. You can even move them to another computer so that you can share music with your friends! 
Please visit [my blog](http://blog.aniosoft.com)for further information.

---

### Post by Uchiha_madara on 2008-08-12
Execuse me but with wine it doesn't work

i tried that

the installation is correct but the Application did not work

i used wine the Last version 1.1.2 

try to use banshee 

I heard that banshee Faces itunes "are the same"

---

### Post by houbysoft.xf.cz on 2008-08-12
Hi, by the way, you may want to sign the iTunes on Linux petition : [http://www.petitiononline.com/itmslin/petition.html](http://www.petitiononline.com/itmslin/petition.html).

---

### Post by ReddogOne on 2008-08-13
> **Uchiha_madara said:**
> try to use banshee 

For this (and other suggesting) iTunes alternatives... can any sign onto the iTunes store?

---

### Post by Nepherte on 2008-08-13
I don't think any of the existing alternatives can work with the iTunes store.

---

### Post by snaggletooth on 2008-08-16
If you do decide to follow this page: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Just know that there's an error there. I'm not sure how to send it in, but maybe one of you guys can help out:

The Firewire GUID command is a bit off.

This is the command that they recommend you use:
```
sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16 | xargs printf "FirewireGuid: 0x%sn" > SysInfo
```

But, that adds an extra 'n' to the end of the code.

I think the author meant for it to be a 'newline' character...

-- Nick


P.S. This is the same case with the ipod-convenience package.



Oh, btw, if you don't know what the GUID is used for, it's for successfully syncing music.

---

### Post by steveydoteu on 2008-08-16
> **stevecov said:**
> Hey guys,

I need to get Itunes 7.7 on my ubuntu so I can use my Ipod without logging onto windows vista so i need it to recognise the Ipod touch. I need 7.7 to use the applications feature, is this possible? All help is much appreciated, thanks!

Get an OGG friendly player ;)

---

### Post by emid on 2008-08-23
> **stevecov said:**
> Hey guys,

I need to get Itunes 7.7 on my ubuntu so I can use my Ipod without logging onto windows vista so i need it to recognise the Ipod touch. I need 7.7 to use the applications feature, is this possible? All help is much appreciated, thanks!

Your best bet as far as I'm aware is to use Vmware.  I know it seems like overkill to boot into a virtual windows OS just for iTunes, but I'm not really sure there is another way to do this from inside Ubuntu at this time.  This is the solution that I found works for me with my iPhone.  It isn't ideal, but it gets the job done.

---

