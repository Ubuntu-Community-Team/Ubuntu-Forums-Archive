---
title: "Canon Pixma iP1600 Installation Problem"
date: 2009-05-09
forum: Hardware
---

### Post by dobber1978 on 2009-05-09
Ok, so I am working on getting my printer working and am having no luck. Fairly new to Linux so this might be my issue.

I have found instructions posted here on how to get my printer to work.

[http://ubuntuforums.org/showpost.php?p=6276893&postcount=1]("http://ubuntuforums.org/showpost.php?p=6276893&postcount=1")

Followed the commands line by line and everything works until I get to the second command to convert rpms to debs where I get this warning

sudo alien cnijfilter-ip2200-2.60-1.i386.rpm
Warning: Skipping conversion of scripts in package cnijfilter-ip2200: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
cnijfilter-ip2200_2.60-2_i386.deb generated

Just a warning so I continued on and finish the rest of the commands, modifying the cupsys restart to cups restart as mentioned in another post I found.

Go on to set up the printer and I find the driver and printer and everything seems to be ok but no test page gets printed upon the, get the pop up box that tells me that it was printed successfully but nothing out of the printer.

If anybody has a suggestion I am all ears.

Thanks
Jeff

---

### Post by dobber1978 on 2009-05-11
Does not seem to be too many people with answers for the printer questions, 

Can anyone tell me how to use the scripts parameter? to include the scripts?

Thanks
Jeff

---

### Post by Sefianix on 2009-05-11
I'm not a linux guru by any means but I thought I'd give you something to try to get you going quicker....

the error is suggesting you may need to use the --scripts parameter in the command you tried to run ... so try:

```

sudo alien --scripts cnijfilter-ip2200-2.60-1.i386.rpm

```

Also, you may try look at the manual for alien by typing:

```
man alien
```

Pretty much any command can be learned about by doing ```
man [some-command]
```

Hope that helps!

---

### Post by pdc on 2009-05-12
do you mind trying the command

> sudo /etc/init.d/ccpd restart

and seeing if that helps?

---

### Post by dobber1978 on 2009-05-12
ok, so I ran the command with scripts and it did not help, I get no warning messages now but I still can print,

I tried the ccpd restart and it tells me that the command is not found.

Jeff

---

### Post by vampiremind on 2009-05-13
I have the same problem... I also do [http://ubuntuforums.org/showpost.php?p=6276893&postcount=1](http://ubuntuforums.org/showpost.php?p=6276893&postcount=1) everything in this but and I also have theese warnings... Also I see when try to install libxml1 it says that cant be found... i try to install libmxl2 and it says its allready the newest version... And finally I have this [SCREENSHOT](http://prikachi.com/users/silver1337/17p.png). I think its important to say when I go to adding drivers of the printer.. I check the radio button that says something like "to load from PPD file" and i browse it from /usr/share/cups/model the file was canonip2200.ppd (Yes my printer is Canon PIXMA iP1600 but i search drivers for my printer in canon.com and then in google I've seen a post in some forum says: there are no drivers for Canon PIXMA iP1600 but if you have that printer you can use Canon iP2200 drivers and it will work properly...)But for a some kind of reason when I do everything my printer still not work... please help :( (Sorry for my english)

---

