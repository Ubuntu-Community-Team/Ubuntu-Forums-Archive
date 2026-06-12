---
title: "Screen Resolution Intel"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by madflying on 2006-05-01
This is part of my xorg:

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       50-160
        VertRefresh     43-100
        Option          "DPMS"
        Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1200x800" "1152x864" "1152x768" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1200x800" "1152x864" "1152x768" "1024x768"
EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1200x800" "1152x864" "1152x768" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1200x800" "1152x864" "1152x768" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1200x800" "1152x864" "1152x768" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1200x800" "1152x864" "1152x768" "1024x768"
        EndSubSection
EndSection
](*,) 

but i cannot get the screen resolution to higher than 1024x768. Any suggestions?](*,) ](*,) ](*,) 

Thanks

---

### Post by jarrett.wold on 2006-05-01
Comment out the modeline in the Monitor section, if you have problems with the display put it back.  However, most modern monitors should be able to pass along the information that modeline gives.  

> 
Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       50-160
        VertRefresh     43-100
        Option          "DPMS"
#        Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection


---

### Post by madflying on 2006-05-01
display works fine, apart the fact that i cannot use higher definition.... Thanks for the comment

---

### Post by jarrett.wold on 2006-05-01
Yes, but if the only modeline you're supplying is 1024, iirc, it will default to that everytime.

---

### Post by madflying on 2006-05-01
Thanks now it is more clear, but even without that line still does not work.

---

### Post by jarrett.wold on 2006-05-01
In your 
/var/log/Xorg.0.log or /var/log/Xorg.0.log.old

Do you have anything that says roughly "mode clock exceeds DDC maximum" ?

---

### Post by madflying on 2006-05-01
nope nothing like that

(II) I810(0): VESA VBE DDC read failed, is this of any help?

Thanks

---

### Post by jarrett.wold on 2006-05-01
After a bit of googling I found this HOWTO

[http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810)

Edit:  I got that off the error message.

---

### Post by madflying on 2006-05-01
I have tried already all the stuff there.....nothing seems to work.....i think i have one choice left, reinstall but i dont want to do that, what do u reckon?

---

### Post by Jason_25 on 2006-05-01
Remove the modeline.  Then restart GDM and post your _full_ xorg.conf and xorg.0.log.

---

### Post by madflying on 2006-05-01
[QUOTE=Jason_25]Remove the modeline.  Then restart GDM and post your _full_ xorg.conf and xorg.0.log.[/QUOTE]

i can post the xorg.conf, but not the log (too long)...tried to attach it did not work???

thanks

---

### Post by Jason_25 on 2006-05-01
You'll have to tar.gz it or zip it up.

---

### Post by madflying on 2006-05-02
[QUOTE=Jason_25]You'll have to tar.gz it or zip it up.[/QUOTE]

i hope this is going to help

---

### Post by Jason_25 on 2006-05-02
Thanks for that.  The relevant part of your log says this:
```

(II) I810(0): Not using mode "1200x800" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using mode "1152x768" (no mode of this name)

```
You'll simply need to add a modeline for those resolutions because they are non-standard.

---

### Post by madflying on 2006-05-02
[QUOTE=Jason_25]Thanks for that.  The relevant part of your log says this:
```

(II) I810(0): Not using mode "1200x800" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using mode "1152x768" (no mode of this name)

```
You'll simply need to add a modeline for those resolutions because they are non-standard.[/QUOTE]


Like the modeline that you told me to delete, i guess, just I want to make sure that I do the right thing, do not want to waste your time.

Let you know results after work....

Thanks

---

### Post by jarrett.wold on 2006-05-02
[QUOTE=madflying]Like the modeline that you told me to delete[/QUOTE]

No reason to be snooty man, everyone's just trying to help.

---

### Post by madflying on 2006-05-02
[QUOTE=jarrett.wold]No reason to be snooty man, everyone's just trying to help.[/QUOTE]

gotta disapoint you did not workm i have atached new files

---

### Post by Jason_25 on 2006-05-02
Actually, it was _not_ like the modeline I told you to delete.  That modeline was actually for a standard resolution, making it unnecessary.  But clearly since your the expert here, I'll leave you to your own devices.

---

### Post by madflying on 2006-05-02
[QUOTE=Jason_25]Actually, it was _not_ like the modeline I told you to delete.  That modeline was actually for a standard resolution, making it unnecessary.  But clearly since your the expert here, I'll leave you to your own devices.[/QUOTE]

I dont understand, I AM NO EXPERT, i am sorry if i have upset you, i was asking to make sure that i was doing the right thing!!!!

---

