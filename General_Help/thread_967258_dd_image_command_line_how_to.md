---
title: "dd image command line how to"
date: 2008-11-01
forum: General Help
---

### Post by keiffee30 on 2008-11-01
i have had a look at the **man dd** and **dd --help** but can not find what i need to do what i need to do. 

I have also looked at the 'on-line Documentation', and i could see what i need to do but its to a FTP server. 
[B]
'What i need to do' [/B]

I would like to take a hard disk image of PC's and Laptops. I have seen G4L, CloneZiller but can not put the image onto a usb hard drive. 

Could some one please tell me what the command line is to make a image and have it put on a usb drive. The image doesn't have to be zipped, as i have got loads of space. Also this is something i can do after

---

### Post by dcstar on 2008-11-01
> **keiffee30 said:**
> i have had a look at the **man dd** and **dd --help** but can not find what i need to do what i need to do. 

I have also looked at the 'on-line Documentation', and i could see what i need to do but its to a FTP server. 
[B]
'What i need to do' [/B]

I would like to take a hard disk image of PC's and Laptops. I have seen G4L, CloneZiller but can not put the image onto a usb hard drive. 

Could some one please tell me what the command line is to make a image and have it put on a usb drive. The image doesn't have to be zipped, as i have got loads of space. Also this is something i can do after

```
dd /dev/whatever > filename-somewhere
```

Make sure /dev/whatever is unmounted (and therefore not in use).

I think that **partimage** may use dd to create it's images, you may want to try that.

---

