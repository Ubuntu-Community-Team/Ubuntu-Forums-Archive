---
title: "Cd-rw/ dvd roms not reading anything... but it works in windows"
date: 2008-11-20
forum: Hardware
---

### Post by iamthepiratesignal on 2008-11-20
I'm an ultra newb when it comes to ubuntu. I had the help of friend when installing it. My cd-rw/dvd drive is not working at all. i have my hard drive partitioned to run both windows and ubuntu. the drive works in windows. help me eradicate this problem so i never have to use windows again.

thanks 
james

---

### Post by cariboo on 2008-11-20
Your cdrom drive must have worked to install Ubuntu. Can you manually mount a cdrom by typing in a Applications-->Accessories-->Terminal:

```
sudo mount /dev/scd0 /meida/cdrom
```

If this works, then right-click on the cd icon on your destop and select eject volume to eject the cd instead of using the button on the drive.

Jim

---

### Post by iamthepiratesignal on 2008-11-21
thank you jim that worked out wonderfully. at least i got it to read cds. funny thing is though it does read dvds, but when i try to play them neither my vlc or totem does not want to play it. the computer does read that it is a dvd though. any advice you could give me would be awesome.

thanks again

---

