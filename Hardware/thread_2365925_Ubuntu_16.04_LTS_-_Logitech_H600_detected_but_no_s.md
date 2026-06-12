---
title: "Ubuntu 16.04 LTS - Logitech H600 detected but no sound"
date: 2017-07-12
forum: Hardware
---

### Post by wolvyreen on 2017-07-12
[COLOR=#111111][FONT=Ubuntu]I'm quite frustrated at this point. I have tried the solutions that I could find on the net for this problem but nothing seems to solve it.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I am fairly new to Ubuntu but enjoying it thoroughly! The only pain I have is my headset has no sound at all. It is detected just fine in the sound settings and I can select it but there is not sound.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have tried re-pairing as suggested in other topics but to no avail. I have tried completely removing this thing called unity and re-installing it but same thing. So then I installed something called pulseaudio volume control and I noticed it shows "Headset (Unplugged)" which I have no clue if it means anything.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I built a Windows 10 VM machine on the ubuntu localhost and the headset works perfectly there. No issues at all.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]PLEASE could someone assist me in trying to figure out why this is happening? It is frustrating me endlessly.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance.[/FONT][/COLOR]

---

### Post by wolvyreen on 2017-07-12
I found the solution to my problem on this link:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)


Step1 solve it for me when I ran this command:


> sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`


---

