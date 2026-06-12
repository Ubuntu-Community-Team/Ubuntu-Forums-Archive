---
title: "Installing Lynis screwed up me pc"
date: 2020-09-29
forum: Hardware
---

### Post by sofasurfer on 2020-09-29
I installed Lynis (security auditing tool) and now my pc desktop is a differant color. And when I enter password the screen gets all scrabbled and slow for a few minutes. Any idea why?

---

### Post by sofasurfer on 2020-09-29
Fixed it. I uninstalled Lynis and had to reinstall my desktop.

---

### Post by cisofy on 2020-09-29
Lynis does not make changes to the system, so as the author I'm puzzled why you state Lynis screwed up your pc. Must be more to it then just the installation of Lynis. Try installing it again on your freshly installed desktop. Does it do the same again?

---

### Post by scorp123 on 2020-09-29
> **sofasurfer said:**
> I installed Lynis (security auditing tool) and now my pc desktop is a differant color. And when I enter password the screen gets all scrabbled and slow for a few minutes. Any idea why?

You must have done a lot of other things too, because Lynis does none of that on its own.  And I'm using Lynis a lot on my many 100 servers and other Linux/Unix installations to track down vulnerabilities that my servers might be exposed to.

---

### Post by sofasurfer on 2020-09-30
```
Lynis does not make changes to the system, so as the author I'm puzzled why you state Lynis screwed up your pc. Must be more to it then just the installation of Lynis. Try installing it again on your freshly installed desktop. Does it do the same again? 
```

Here is the instructions I followed to install Lynis. [https://packages.cisofy.com/community/#debian-ubuntu](https://packages.cisofy.com/community/#debian-ubuntu) 
I'll wait to see your response and then I will try to reinstall.

---

### Post by Qassis on 2020-11-21
HOW did you install your Lynis?   I installed from the Synaptic Package Manager, then ran "sudo lynis audit system".  It gave and still gives me a GREAT report and recommendations, but makes no changes other than writing to text logs. I hope you get yours fixed as I LOVE Lynis  and would like to chat about it and other Cyber Security Apps for Linux with Ubuntu users. I'm always trying to find (NON-CyberSecurity Administrators Level) Ubuntu 'user' level Security apps to improve my Linux Home computer. Currently I use Lynis, Firetools/Firejail, ClamAV/ClamTK, and GUFW/UFW and am quite happy with them and trust I've increased my box's security profile by using them.

---

### Post by Qassis on 2020-11-21
Great answers.   As far as I can see, Lynis update required full update, not just signature files as in anti-virus programs.  Is that correct; reinstall for each update? Thank you.

---

