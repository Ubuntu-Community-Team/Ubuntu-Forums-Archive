---
title: "Asus n82jq audio jack not working"
date: 2011-01-18
forum: Hardware
---

### Post by hamid_valad on 2011-01-18
hi every one
i am new with ubuntu, and I've got ubuntu 10.10 for my laptop. but i have problems with it. i appreciate help, step by step... (i apologise)
when i use my laptop to listen to music through devices speakers, it works just fine
but when i plug my headphone to its audio jack, it doesn't play any sound through headphone and plays sound via device's speakers...
can any one help me please?
(i have found [this link]("http://forum.ubuntu-it.org/index.php?topic=410679.0"), but i didn't understand a word out of it!!! it's in Italian (i translated it via google, they solved the problem, but i didn't get how!))

---

### Post by hamid_valad on 2011-01-18
hi

i'm sorry to post different threads but i didn't want to mix things up
i am a beginner in ubuntu and linux and recently i have installed a ubuntu 10.10 on my asus n82jq.
i've got some problems with the drivers.
my internal microphone is not working, i tried to use external mic, but it seems ubuntu does not recognise my mic-in jack! (like mu headphone jack!)
so i wanted some help...
again, i am a beginner and i would appreciate step by step guide. thanks in advance.

---

### Post by hamid_valad on 2011-01-20
hi everyone, I'm getting a little confused...
i asked a question and no one replied to me!!!!
even though put a link with a guide (but it wasn't clear for me because i'm very new in this business) but nobody helped me?!
i dont know what to do.
plz help me

---

### Post by hamid_valad on 2011-01-20
hi everyone
u mean no one knows what should i do?!
please help me!

---

### Post by overdrank on 2011-01-20
Threads merged. :)

---

### Post by lidex on 2011-01-21
> **hamid_valad said:**
> hi everyone
u mean no one knows what should i do?!
please help me!
Could use a little more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by hamid_valad on 2011-01-22
> **lidex said:**
> Could use a little more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

thanks man
here is the link provided
[http://www.alsa-project.org/db/?f=474fa17c050ee43ed2eb40a8688c3b6a1fb199e5](http://www.alsa-project.org/db/?f=474fa17c050ee43ed2eb40a8688c3b6a1fb199e5)
i'm looking forward to your help


plus
how can i make any changes to alsa-base.conf

---

### Post by lidex on 2011-01-23
> **hamid_valad said:**
> thanks man
here is the link provided
[http://www.alsa-project.org/db/?f=474fa17c050ee43ed2eb40a8688c3b6a1fb199e5](http://www.alsa-project.org/db/?f=474fa17c050ee43ed2eb40a8688c3b6a1fb199e5)
i'm looking forward to your help


plus
how can i make any changes to alsa-base.conf

More later, but for now do a system update. I'm pretty sure there is a newer kernel available for you. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now reboot. Finally post this output:
```
uname -a
```

---

