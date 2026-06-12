---
title: "Microphone not working on chromebook with chubuntu loaded"
date: 2013-01-19
forum: Hardware
---

### Post by JPRedmond on 2013-01-19
HELP! I've loaded an Acer C7 chromebook with chubuntu 12.04 and can't get the microphone to work. I've looked at other posts and tried them all with no luck. Has anyone had the same problem and if so what was the fix?

Thanks

---

### Post by digimark on 2013-01-20
Same problem with me...damned annoying.....its almost as if the pulse audio isnt working...but outpu sound is fine.....

---

### Post by JPRedmond on 2013-01-20
I agree digimark. Because of this I can't get SKYPE to work :(

---

### Post by jacs101 on 2013-02-06
here is the work around for the mic.
[FONT=Courier New]wget [http://www.cisgendered.com/~keyvin/mic-fix.deb](http://www.cisgendered.com/~keyvin/mic-fix.deb)
sudo dpkg -i mic-fix.deb
sudo shutdown -r now[/FONT]
[FONT=Courier New]make sure to use speaker icon top right corner of desktop to raise input volume to 100%[/FONT]

---

