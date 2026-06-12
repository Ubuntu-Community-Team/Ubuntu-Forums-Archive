---
title: "No sound in lucid with realtek alc 883"
date: 2010-10-25
forum: Hardware
---

### Post by Skyline649 on 2010-10-25
[b][size="4"]hello,

i just upgraded to lucid ,and i don't have any sound,in the sound tab i should get on the tab output , where the connector is , internal speakers,

can anyone help me [/size][/b]

---

### Post by lidex on 2010-10-25
Make sure any old audio config files are removed:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Next. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Skyline649 on 2010-10-26
I do all the steps, but now it's worst, i don't have any sound to respond, when i click on the sound tab :s

---

### Post by lidex on 2010-10-26
Where is your alsa-info script output? I need that to help you.

---

### Post by Skyline649 on 2010-10-29
> **lidex said:**
> Where is your alsa-info script output? I need that to help you.


what should i write in the terminal to get the script?

---

### Post by fallenshadow on 2010-10-30
As an easy solution I recommend you upgrade to Ubuntu 10.10 because sound support I found was very, very bad in Ubuntu 10.04.

Now im happy that sound is working well for me with Ubuntu 10.10!  :guitar:

---

### Post by Skyline649 on 2010-10-30
> **fallenshadow said:**
> As an easy solution I recommend you upgrade to Ubuntu 10.10 because sound support I found was very, very bad in Ubuntu 10.04.

Now im happy that sound is working well for me with Ubuntu 10.10!  :guitar:


Yes, i know that, but the problem is, when i upgrade to 10.10 i loose my WIFI and instead of that i got sound :d

---

