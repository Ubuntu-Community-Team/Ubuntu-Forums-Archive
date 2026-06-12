---
title: "Firefox plays up the video but not the sound"
date: 2008-08-04
forum: General Help
---

### Post by realizee on 2008-08-04
Hi, I recently installed Firefox 3.0, and I was browsing in youtube when i realized that the video works but not the sound and it doesn't prompt me to install Flash . Why ? :P

---

### Post by trevelyan on 2008-08-04
close firefox and then type this in a terminal
```
sudo killall pulseaudio
```
after that try youtube again. i do that command everytime i boot up ubuntu.

---

### Post by realizee on 2008-08-04
Kinda annoying to do that?

---

### Post by mb_webguy on 2008-08-04
Try this:
```
sudo apt-get install libflashsupport
```

This package fixes some incompatibilities between Flash and PulseAudio.

---

### Post by trevelyan on 2008-08-04
> **realizee said:**
> Kinda annoying to do that?

did it work? 
yes it is annoying.

---

### Post by realizee on 2008-08-04
yes it worked thanks so much haha :D

---

### Post by shimi on 2008-08-04
I had a similar [flash problem with firefox]("http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html").

Great to hear that you solved your problem. Mark this Thread as SOLVED so others would know that this Thread contains a solution to the problem.

---

