---
title: "burn cd from console"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by wmantly on 2007-08-01
is there a way to burn a cd from an .ISO from the console? The only working pc w/ a cd burner right now is running ubuntu server.

---

### Post by eggdeng on 2007-08-01
There's a program called cdrecord. The syntax runs something like ```
mkisofs -R -l my_folder \ | cdrecord -v dev=my_cdrom speed=n
``` where my_folder is a directory you have copied the file to and want to copy it from (the directory itself is not copied) and n is an integer representing the speed you want to record at e.g. 8 for 8x. I have never used cdrecord so check this out with other sources or you might end up with spindle full of coasters.

---

### Post by eggdeng on 2007-08-01
Edit: Probably need to use sudo with this.

---

### Post by wmantly on 2007-08-01
thanx, im going to try it out now, i only need one cd to get my current pc up and running again.

---

