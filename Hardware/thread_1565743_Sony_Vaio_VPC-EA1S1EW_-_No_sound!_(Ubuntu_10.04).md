---
title: "Sony Vaio VPC-EA1S1E/W - No sound! (Ubuntu 10.04)"
date: 2010-09-01
forum: Hardware
---

### Post by joaohomem on 2010-09-01
Hello everyone. I had installed the Ubuntu 10.04 and I noticed that the audio system didn't work. I can't hear no sound! My Laptop is a Sony VPC-EA1S1E/W. What can i do to make it work correctly?

Greetings,

joaohomem

---

### Post by zecapistolas on 2010-09-01
Check if the version of alsa instaled is 1.0.23....

---

### Post by joaohomem on 2010-09-01
I'm not very used to this OS. So, can u explain me how to do that? 

BTW, zecapistolas are you portuguese?

---

### Post by ivanovnegro on 2010-09-01
Could you check your sound preferences?
Maybe something is muted.

---

### Post by joaohomem on 2010-09-01
I've already checked that! The sound is not muted. Maybe it's a hardware incompability. But I don't know what drivers should I install! Did you know if any VAIO have the same problem that I noticed?[]("http://ubuntuforums.org/showthread.php?t=361237")

---

### Post by ivanovnegro on 2010-09-01
> **joaohomem said:**
> I've already checked that! The sound is not muted. Maybe it's a hardware incompability. But I don't know what drivers should I install! Did you know if any VAIO have the same problem that I noticed?[]("http://ubuntuforums.org/showthread.php?t=361237")

Ok. Now could you tell me how you noticed that you have not sound? What were you doing, maybe playing a track?
If so you need to install the non-free codecs to be able to play for example mp3s. That happened to me the first time.
You need for that the restricted packages.

---

### Post by joaohomem on 2010-09-01
It's not the non existence of the mp3 codec. I can't hear sound at everything I'm doing. No system sound. No sound while I'm watching youtube videos or playing music at any format. If it was from mp3 codec, I would solve it very quickly, as I'm used do to the same thing to video and audio formats that I couldn't play while I'm using the OS that I often use (Windows).

---

### Post by ivanovnegro on 2010-09-01
> **joaohomem said:**
> It's not the non existence of the mp3 codec. I can't hear sound at everything I'm doing. No system sound. No sound while I'm watching youtube videos or playing music at any format. If it was from mp3 codec, I would solve it very quickly, as I'm used do to the same thing to video and audio formats that I couldn't play while I'm using the OS that I often use (Windows).

Ok, its more complicated then I expected.
And I havent got a Vaio.
Maybe youre right and you need proprietary drivers.
You can try to find something in the forums about Vaio machines. There will be more information.
And I think you need maybe alsa 1.0.23 like zecapistolas said.
And you could go to system preferences and check for proprietary hardware drivers.

Update: [Here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") is the alsa update script.

---

### Post by joaohomem on 2010-09-01
Maybe you are completely correct. I've check a page that tells me how to solve my problem. The problem is on the Advanced Linux Sound Architecture (ALSA), as someone said. Apparently, Ubuntu 10.04 is loaded with the old version of ALSA, which fails to play most of the audio devices. To solve this problem we need simply to upgrade to the latest version of ALSA. After that the problem should be solved. I found a page that explains me how to do that so I will do it. In the end, I'll tell to you if I had my problem solved.

The pages that I saw, were:
[http://www.bytechip.com/2010/07/ubuntu-sony-vaio-audio/](http://www.bytechip.com/2010/07/ubuntu-sony-vaio-audio/)
and after that
[**http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/**]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

---

### Post by joaohomem on 2010-09-01
Unfortunately, I've done everything that they tell us to do when we want to update ALSA from version 1.0.21. to version 1.0.23. but when I put in the terminal:
> cat /proc/asound/versionto check ALSA's version, the answer is
> Advanced Linux Sound Architecture Driver Version 1.0.21.
So how do you advice me to update ALSA to version 1.0.23.?

---

### Post by ivanovnegro on 2010-09-01
> **joaohomem said:**
> Unfortunately, I've done everything that they tell us to do when we want to update ALSA from version 1.0.21. to version 1.0.23. but when I put in the terminal:
to check ALSA's version, the answer is

So how do you advice me to update ALSA to version 1.0.23.?

Thats strange, tell me step by step how you upgraded to see the fault or why it didnt work.

---

