---
title: "Nvidia card not working right"
date: 2008-08-30
forum: General Help
---

### Post by Jungle-Cat on 2008-08-30
Hello,
I'm trying to use Cedega... using Ubuntu on previous occasions I've had no problems at all.

I'm now using Kubuntu with KDE4... I've installed the nvidia proprietary drivers using the driver manager, and it appears to be running fine (I have proper screen res, and nvidia-settings shows everything up correctly).

However, in Cedega, the video tests fail. Also, it may be worth nothing that the only thing cedega picks up about my video card is that it has 128mb of memory... it does not detect that it is a 6600GT nvidia card, or anything else. nvidia-settings does find all that, and that it is a 6600GT.

Currently this is my only technical problem... Any help would be appreciated.

Thanks

/edit
I went to run tests again, but went to them through a different menu. It said stuff about 64bit and needing 32bit emulation (I should have said im using amd64 kubuntu kde4...).
So I searched considering this and found:
[http://ubuntuforums.org/showthread.php?t=491370](http://ubuntuforums.org/showthread.php?t=491370)
I can't use "sudo kate /etc/environment" as I would "sudo gedit /etc/environment"... I can't find a way to edit environment as root!

/edit
Ok I just used apt to install gedit... worked fine. The above thread has it all in it, you just need to run apt-get install ia32-libs, make that ln if need be and voila!

---

### Post by arch0njw on 2008-08-31
I'll take a moment to be dense.  Are you all set now?

---

