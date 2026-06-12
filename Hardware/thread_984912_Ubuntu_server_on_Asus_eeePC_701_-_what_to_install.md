---
title: "Ubuntu server on Asus eeePC 701 - what to install?"
date: 2008-11-17
forum: Hardware
---

### Post by izvir on 2008-11-17
Hello guys!
I have an Asus eeePC 701 laptop which I will use to make a home server for my website. I will be using it only for this task, so I'm thinking of installing Ubuntu server. I know I could use eee Ubuntu, but I need something more lightweight.

So, my question is, what packages do I need to install, to make these things work:
- ACPI (automatic frequency scaling, turning the LCD off...)
- Wireless and WPA encryption

Best regards to you all!

---

### Post by starcannon on 2008-11-17
You'll want the kernel and perhaps a few of the packages from [http://www.array.org](http://www.array.org)
Then perhaps a LAMP server, though maybe not, just use the server edition of Ubuntu, or even the net install, and grab Apache, that'd be where I'd start; though I would likely use something much less cool for the project lol. I love my Eee's, I have the 700, two 701's, and a 702(8g), a cloudbook(via gpu... it'd make a good server, and utilizes a replaceable hdd, want to trade?), and I the newest arrival here at my house, a Dell Mini9(this thing rocks).

GL, and seriously if you would be interested in a trade, cloudbook with 1gb of ram, and a 60gb hdd for the asus 701 we could chat, feel free to pm me if interested. 

Anyway, minimal install or server install, apache, and array.org kernel and select packages should allow you to do your project on the eee.

Have fun!

---

### Post by izvir on 2008-11-17
Thanks for your help, really appreciate it! I will go with server install. But I still need to know, what packages I need for wireless, WPA encryption and ACPI.

And yeah, I too love my eeePC!

---

### Post by starcannon on 2008-11-17
> **izvir said:**
> Thanks for your help, really appreciate it! I will go with server install. But I still need to know, what packages I need for wireless, WPA encryption and ACPI.

And yeah, I too love my eeePC!

Wireless with WPA support is built into the array.org kernel if I remember correctly, if not they have the packages there as well, ACPI the whole #! is handled. 

Heres a clicky link, its all about the eee nothing else there:
[http://array.org/ubuntu/](http://array.org/ubuntu/)

enjoy.

---

### Post by izvir on 2008-11-17
Thanks! Really owe you one! ;)

---

### Post by starcannon on 2008-11-17
anytime! thats what makes these forums great :)

---

### Post by izvir on 2008-11-18
Well I have the system up and running! And it works lightening fast :)
The only problem I have is to setup the cpufreqd. It responds with "no cpufreqd socket found". Has anyone had the same problem? The ACPI is working so I really don't know where the problem is.

Best regards!

---

