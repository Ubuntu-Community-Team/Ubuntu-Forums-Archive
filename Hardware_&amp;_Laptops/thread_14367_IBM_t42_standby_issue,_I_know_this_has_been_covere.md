---
title: "IBM t42 standby issue, I know this has been covered but I cant figure it out"
date: 2005-02-06
forum: Hardware &amp; Laptops
---

### Post by faceplate on 2005-02-06
Hello everyone, I am trying to get suspend to ram working on my t42, I have searched these forums for the command to enter into the console, but for the ones I have tried I get a "permission denied" message and this includes running the command with "sudo" By the way I am running hoary. Thanks 

Also one quick additional question, all my icons on the desktop and in nautlis have changed to a "sheet of paper icon" I think this may have happened after I updated my computer. not upgrading to hoary just a regular update. Anyone know how I can fix this? thanks

---

### Post by malmjako on 2005-02-07
Try ```
sudo su
```and then issue the command again. Or you can change permissions on the file you're trying to write to, ```
chmod go+w /proc/acpi/fileyouwanttowriteto
```

---

### Post by faceplate on 2005-02-07
Thanks, the command you gave me worked and allowed me to run 

```
 echo mem  > /sys/power/state
``` 

the system goes into standby just fine, when I come out of standby my LCD powers on but there is no image. I tried plugging in a external monitor to my laptop and the picture is there when I come out of standby. Is there a different command I should be using to go into standby? After coming out of standby I tried using Ctrl+ALT+Backspace to restart gnome but it still sends to picture to the external monitor. I also tried switching terminals with Ctrl+Alt+F1/F2/etc but that just shows me a black screen. Any ideas? thanks. By the way I usually dont have this external monitor plugged in.

---

