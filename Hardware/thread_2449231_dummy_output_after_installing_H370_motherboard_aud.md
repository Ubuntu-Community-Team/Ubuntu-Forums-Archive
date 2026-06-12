---
title: "dummy output after installing H370 motherboard audio driver"
date: 2020-08-22
forum: Hardware
---

### Post by mcrose on 2020-08-22
Hi all
unfortunately I downloaded a installer form [https://www.msi.com/Motherboard/support/H370-GAMING-PLUS](https://www.msi.com/Motherboard/support/H370-GAMING-PLUS) for audio-driver but I got problems trying to install
(yep, the default config installed by budgie was working ok)

I wrote to them and after showing them (because the asked) a error-printscreen , they pointed my to download a installer from [realtek.com]("http://realtek.com/")

well I also had problems with that installer and still waiting for response


the first installer erased, removed, delete, whatever configuration I had

I removed, purged and re-installed alsa and pulseaudio packages
I tried almost 20 solutions around internet
**none of them** would returned me sound configuration

I could add all pages read, but I closed them all (the tabs)

last thing I tried was subjected in budgie's forum: re-start with and older kernel version (40 and 26, currently I have 42), didn't work

this is my PC info:
```
&#10095; cat /etc/issueUbuntu 20.04.1 LTS \n \l


&#10095; cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

&#10095; uname -a
Linux home 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

&#10095; sudo systemctl status alsa-state.service
[sudo] password for mcrose: 
&#9679; alsa-state.service - Manage Sound Card State (restore and store)
     Loaded: loaded (/lib/systemd/system/alsa-state.service; static; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:alsactl(1)




```

so, this is my last change before I re-install the whole OS (please, don't tell me to do so unless... )

---

### Post by CelticWarrior on 2020-08-22
Welcome.

Windows drivers are NOT to be installed anywhere else but the Windows versions they were coded for.
Linux distros already come with most required drivers in the kernel. Rarely users have to install additional drivers and even rarer for audio related devices.
No, we don't usually need to install drivers from Realtek.

At this point reinstalling the OS is likely to be faster and give better results than anything else. We don't know what you actually installed and the output provided isn't helpful.

---

### Post by mcrose on 2020-08-22
windows drivers ?

---

### Post by CelticWarrior on 2020-08-22
> [COLOR=#000000]unfortunately I downloaded a installer form [/COLOR][https://www.msi.com/Motherboard/supp...70-GAMING-PLUS]("https://www.msi.com/Motherboard/support/H370-GAMING-PLUS")[COLOR=#000000] for audio-driver but I got problems trying to install[/COLOR]
[COLOR=#000000](yep, the default config installed by budgie was working ok)[/COLOR]

The above links has drivers for Windows 10 exclusively.

---

### Post by mcrose on 2020-08-22
[FONT=&quot]just to make a point on the motherboard version end site[URL="https://www.msi.com/Support_search/h370%20linux/technical/download"]

https://www.msi.com/Support_search/h370%20linux/technical/download[/URL] 
[/FONT]
[FONT=&quot][URL="http://download.msi.com/dvr_exe/Realtek_6.0.1.5618.zip"]
http://download.msi.com/dvr_exe/Realtek_6.0.1.5618.zip[/URL][/FONT]
[FONT=&quot]
I guess I'm losing time reading you, been and ubuntu addict/lover didn't meant you could solve my problem

thanks anyway[/FONT]

---

### Post by CelticWarrior on 2020-08-23
MSI as almost all vendors make their products for Windows. So, first thing you must understand is that the links above are for WINDOWS. **Absolutely NOTHING in the links above is applicable to Ubuntu.** The Realtek zip does include a "linux" folder with generic Linux drivers from 6 years ago! NOT APPLICABLE to any currently supported Ubuntu release and the current kernel already includes drivers for your sound card/chipset as you know - *[COLOR=#000000]the default config installed by budgie was working ok[/COLOR]*[COLOR=#000000]- and you should have kept things like that, end of story.

Again,
> [/COLOR][COLOR=#000000]**At this point reinstalling the OS is likely to be faster and give better results than anything else.** We don't know what you actually installed and the output provided isn't helpful.[/COLOR][COLOR=#000000]

This is the best help that can be given, a reality check. Reinstalling the OS takes minutes. Please don't blame others for the time *you're* wasting.[/COLOR]

---

### Post by tea for one on 2020-08-23
> **mcrose said:**
> 
(yep, the default config installed by budgie was working ok)

the first installer erased, removed, delete, whatever configuration I had

I removed, purged and re-installed alsa and pulseaudio packages

I tried almost 20 solutions around internet

**none of them** would returned me sound configuration

Given the description of this recent activity, it would be impossible for a forum member to quickly diagnose and offer a concrete solution.

I agree with CelticWarrior that your quickest and most reliable course would be to re-install Ubuntu and then add your back-up data.

---

### Post by Yellow Pasque on 2020-08-24
> **mcrose said:**
> I guess I'm losing time reading you, been and ubuntu addict/lover didn't meant you could solve my problem

That is incredibly rude. 
Also, the "ubuntu addict and loving it" is a silly thing this forum does: "The images, their colors, and the changing icons don't have any special meaning. They simply change as time goes by. You will see (among other things) green coffee beans, roasted (brown) coffee beans, various sorts of coffee cups and mugs and so on. Like the titles, nothing specific is implied by the presence of specific images or titles (in almost all cases...staff, admins and banned users are some of the exceptions). **These items are for fun, and are not serious**. They are not a rank of any kind." -- [https://ubuntuforums.org/showthread.php?t=1006656](https://ubuntuforums.org/showthread.php?t=1006656)

---

