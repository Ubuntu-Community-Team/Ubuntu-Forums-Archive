---
title: "How to Uninstall Studio from Log in Terminal"
date: 2008-09-29
forum: General Help
---

### Post by kystorms on 2008-09-29
Okay this is a desperate situation

my kids pc has been updated to Ubuntu studio, but the nvidia card wont let the screen resolution be small enough for us to actually log INTO studio, the log in screen graphic is off the reachable usable screen area, I can not seeem to curse/tab to the log in area

how can i uninstall studio from the log in terminal????

please any help as fast as possible will be great

---

### Post by eZtaR on 2008-09-29
Here you go :)
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by kystorms on 2008-09-29
well, i acutally was able to successfully remove the studio splash screen buit not after it says kubuntu - there is just a black screen, NO LOG page now, so I guess I need to know the code to install a splash screen to log in with, any ideas?

thanks

---

### Post by eZtaR on 2008-09-29
this should do the trick (taken from [this thread](http://ubuntuforums.org/showthread.php?t=205002))
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

