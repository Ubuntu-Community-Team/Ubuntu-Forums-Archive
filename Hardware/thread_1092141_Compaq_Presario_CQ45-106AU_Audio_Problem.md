---
title: "Compaq Presario CQ45-106AU Audio Problem"
date: 2009-03-10
forum: Hardware
---

### Post by anetizen on 2009-03-10
Hi All,

I installed Ubuntu 8.10 on my Compaq Presario CQ45-106AU Laptop. Everything works fine except facing mazor problem in display & audio section.

1. display driver activated and working properly but the screen is scrolling sometimes from left to right, which I not able to manage.

2. Audio driver detected by the system but no output is comming from the speaker. I tried to test it through audio configuration as well as by running audio player but no sound at-all from the speaker in full volume.

Please help me to resolve the issue, as I am facing from a long.

Regards,

Saurav

---

### Post by dhruvasagar on 2009-05-12
I edit my /etc/modprobe.d/sound file and put this :
```

options snd slots=snd-hda-intel,snd-hda-intel
options snd-hda-intel model=dell-m4-2
# 5Dex.Jpa__qQ4asA:SBx00 Azalia (Intel HDA)
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel
```

This sorted out my audio problems. I noted that model=dell-m4-1 worked equally well instead of the model=dell-m4-2 as shown above.

Hope that helps you.

---

### Post by dhruvasagar on 2009-05-12
I also went to System->Preferences->Sound and selected ALSA Advanced Linux Sound Architecture for all and HDA STI SB as the default mixer

---

### Post by topcoder on 2009-06-03
Visit this link: [http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

I too have the same laptop, same things apply.

---

