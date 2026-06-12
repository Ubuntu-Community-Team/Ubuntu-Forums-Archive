---
title: "Using the Unmount Command"
date: 2009-04-02
forum: Hardware
---

### Post by Steve R. on 2009-04-02
I have the old UBUNTU install CD in the CD.  In order to remove it, I received the error message that ROOT has to unmount the device.  When I enter "sudo unmount /dev/scd0" I am told that there is no such command! 

I assume that means that my profile is incorrect.  I took a quick look at my .profile, but I couldn't tell if anything was wrong.

---

### Post by doas777 on 2009-04-02
it's 
'umount' 
the rest of your command should work.
good luck

---

### Post by Steve R. on 2009-04-03
Thanks.  For those of us who are visually impaired, we need a braille vision!!!

---

### Post by doas777 on 2009-04-04
sorry man, I should have used a code tag. the full command would be:
```

sudo umount /dev/scd0 

```

---

### Post by Steve R. on 2009-04-04
Not a problem.  Using Windows has "*destroyed*" my ability to use the command line.  Also my vision has become really bad.

---

