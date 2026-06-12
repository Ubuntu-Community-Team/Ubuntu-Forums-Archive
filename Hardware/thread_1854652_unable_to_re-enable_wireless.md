---
title: "unable to re-enable wireless"
date: 2011-10-04
forum: Hardware
---

### Post by BS_Kustomz on 2011-10-04
hello, i am running Natty on Compaq presario CQ60, now...

i have a recent thing, like people that go back and read the classic novels they haven't read... yeah well, i have been going back and listening to the classic albums i never listened too

now that that's out of the way... i was laying in bed listening to rhythm box on battery power. too conserve battery i figured i would turn the wireless off with the wireless button (something i have done before) only every other time i have turned it back on before shutting down... this time i didn't

the album was over so i opened the lid and hit the power button (i have it set to shutdown on the power button press) took my head phones off and went to sleep

the next morning i plug it in and power up, only this time i didnt get the "PASSWORD FOR KEYRING" prompt to log on to my wi-fi, so i went up to the top and got this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=203564&stc=1&d=1317772959[/IMG]
i ran the IWCONFIG and got this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=203565&stc=1&d=1317772959[/IMG]
now i did fiddle around with the button and got it to say go back and forth between the "disabled by hardware switch" and just plain old "disabled" like so but still after checking the "enable wireless" selection it does nothing
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=203566&stc=1&d=1317772959[/IMG]
but now after start up if i try to press the hardware button it stays on "disabled by hardware switch" until i restart

is there a direct way around this that i can just force the wireless on? or a way to fix the button?

---

### Post by BS_Kustomz on 2011-10-05
nothing? no ideas? isnt there a "sudo turn this damn thing on" command?

---

### Post by lcman on 2011-10-05
> **BS_Kustomz said:**
> nothing? no ideas? isnt there a "sudo turn this damn thing on" command?

Try checking and unchecking Enable Wireless. Also try ifup wlan2

---

### Post by diasf on 2011-10-05
sudo iwlist wlan2 scanning

Not sure why would work, but it makes my wifi connect when sometimes it weirdly doesn't want to

---

### Post by BS_Kustomz on 2011-10-06
nope, nope,  and nope

---

### Post by BS_Kustomz on 2011-10-06
screw it... blowing it away and starting clean... and supergluing that button

---

