---
title: "DVD Burner no seen"
date: 2013-02-04
forum: Hardware
---

### Post by lpierce65 on 2013-02-04
I'm not sure if My DVD burner is Dead or for some reason  its not seen by Ubuntu.  when I insert a audio cd it never plays even though I have downloaded several player and burner  files..  how do you trouble shoot it , I'm new to  Unbuntu  is there a place to see if the drive is working properly or even there at all ??  I'm also not sure  how Ubuntu turned into Edubuntu  ??

Thanks

Larry Pierce

---

### Post by chellrose on 2013-02-04
Is it an internal or an external DVD drive?

Put a CD in the drive, then go to terminal and type
```
ls /media
```

You should see something like "cdrom" or "cdrom0" (or maybe both).  Then, in the terminal, type
```
ls /media/cdrom
```
(and do the same for cdrom0 if that showed up)

One of those should net you a list of files on the CD.  If nothing shows up on ```
ls /media
```, then it's not recognizing your drive.

What version of Ubuntu are you using?

---

### Post by lpierce65 on 2013-02-05
Its an internal  Sony DVD burner  and I'm  using  12.xx  I'll figure out how to get to terminal mode and try your suggestions  

Thanks

Larry

> **Sissy13 said:**
> Is it an internal or an external DVD drive?

Put a CD in the drive, then go to terminal and type
```
ls /media
```You should see something like "cdrom" or "cdrom0" (or maybe both).  Then, in the terminal, type
```
ls /media/cdrom
```(and do the same for cdrom0 if that showed up)

One of those should net you a list of files on the CD.  If nothing shows up on ```
ls /media
```, then it's not recognizing your drive.

What version of Ubuntu are you using?

---

