---
title: "Nvidia driver snafu"
date: 2013-01-01
forum: Hardware
---

### Post by jackechanprime on 2013-01-01
Hey guys, I've been trying to get EVE online working on my machine, and in the process have managed to uncover that my graphics drivers more closely resemble scrambled eggs then drivers. (well, perhaps not THAT bad, but things ARE all mixed up.)

Apparently the intel integrated chipset as well as the NVIDIA drivers are present and in conflict, and on top of that, the NVIDIA propriatary drivers are in conflict with nouevo (or however it was spelled) drivers.

I'm in way over my head here. I only got to the point that I realized that this is a problem because it's the exact same problem that someone else had on another thread. Unfortunatly for me, said thread went dead as soon as that problem was diagnosed, leaving me up shits creek.

(I know this is sort of out of place but...) If anyone also cares to help with the eventual goal of getting EVE running, I have it fully and functionally installed, it just crashes instantly the second it tries to actually run the game. Eg, launcher=> splash screen (for a few microseconds) => crash. Again, this issue is optional. I'm really more worried about getting my graphics drivers in line.

Forgive me, but you'll have to give me the terminal code to get the name of the intel chiset, but the Nvidia chipset is a GeForce GT 520M. You'll also have to tell me how to tell you what the drivers I have are. Again, sorry for being so horribly nooby. (At least I know that I dont know.)

~Q

---

### Post by jackechanprime on 2013-01-01
Oh, i'm running ubuntu 12.04. Sorry, I always forget that.

---

### Post by grahammechanical on 2013-01-02
The best that I can offer as you seem to have Nvidia Optimus technology is this link to an open source driver.

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

Although this technology has been around for some time Nvidia has failed to provide a Linux driver for it. Nvidia only announced the other month that it was starting work on a linux drvier for its Optimus technology.

Regards.

---

### Post by jackechanprime on 2013-01-02
Thanks, I installed bumblebee, and have seen an improvement.

:( Eve still dosen't work though.

Oh well, i'll head over to the games/leasure forum then.

If anyone else has some mirical fix, then please dont hesitate to post, I'll be checking for a few days at least.

---

### Post by Yellow Pasque on 2013-01-04
So you're running Eve with optirun command? What do these commands do?
```
sudo apt-get install mesa-utils
glxinfo
glxgears
optirun glxgears
```

---

