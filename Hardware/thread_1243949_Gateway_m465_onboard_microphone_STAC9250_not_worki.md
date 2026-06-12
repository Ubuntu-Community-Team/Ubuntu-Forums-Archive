---
title: "Gateway m465 onboard microphone STAC9250 not working"
date: 2009-08-18
forum: Hardware
---

### Post by raulpober on 2009-08-18
Hello,

I'm running alsa v1.0.20, kubuntu 9.04, and linux kernel 2.6.28-14. I have been working on getting the onboard microphone working on my Gateway m465 laptop today. I have followed the ALSA upgrade guide: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) and the troubleshooting steps at [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)  and tried all of the different model types for the STAC9250 listed here [URL="http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/HD-Audio-Models.txt;h=4c95a6c3f79fe7c44e5b9026a0536542feb9eaf4;hb=cf341443f2b63c93fe6741967d1004021492e78d"]https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblemshttp://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/HD-Audio-Models.txt;h=4c95a6c3f79fe7c44e5b9026a0536542feb9eaf4;hb=cf341443f2b63c93fe6741967d1004021492e78d
[/URL] 
All of the other audio features are working fine, including capture input through the jack. It seems that alsa does not recognize there is a second capture input available. Has anyone experienced this problem before? 

Thanks!

Paul

---

