---
title: "hardware boot problems e1505"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by discord on 2007-01-16
I have an e1505 which I purchased in June 06. It is the original core duo. Sometimes when I turn it on the fan is running at full even from a cold boot. The laptop is not overheating nor hot, but it runs really slow with the fan still on full blast. If I login to ubuntu then shut down the fan will turn off and the laptop runs fine. I've done a google search but couldn't find anyone with a similar issue. Has anybody experienced this or know how I can get dell to fix the problem?

---

### Post by frankx on 2007-03-10
Hello, yes I have experienced the same problem with the Dell Inspiron E1505 Intel Core Duo T2300 running Windows Media Center 2005. The boot is extremely slow, the fan runs constantly, and once up everything runs slow with the cpu staying at 60% or higher with little running. Smells like a virus to me, except for the fan running all the time.

---

### Post by frankx on 2007-03-10
Hello, yes I have experienced the same problem with the Dell Inspiron E1505 Intel Core Duo T2300 running Windows Media Center 2005. The boot is extremely slow, the fan runs constantly, and once up everything runs slow with the cpu staying at 60% or higher with little running in the way of programs. Smells like a virus to me, except for the fan running all the time.

Well, I found out the cause in this case. It wasn't a virus, but the virus protection. My daughter added a second virus protection program. Once we deleted the unwanted virus scanner, the problem was fixed. In this case she had both McAfee (which came with the laptop) and Norton (which was required by her college). We chose to remove the McAfee only because Norton was required at school and things improved immediately on the next boot. Boot was very fast, cpu usage is low, and the fan rarely comes on now.

We had another problem (before removing the extra antivirus program) trying to access the Control Panel from the Start menu. It would give an error stating: "Runtime error! This application has requested the Runtime to terminate it in an unusual way. Contact the applications support team." Internet searches mentioned removing the Google toolbar, but this laptop did not have that toolbar. This problem no longer occurred after removing the second antivirus program.

Hope this helps your situation.

---

### Post by JediLow on 2007-03-18
I actually think that its due to a faulty heat sensor... in my experience this only happens (haven't tried it yet with Ubuntu - just got it running today) when the laptop comes from a cold boot from a cold environment, if you hit the FN+Z buttons than the laptop which resets the fan sensors then fans will stop (however the speed throttling doesn't turn off).

Its definitely not an antivirus/virus problem (since I know a couple computers which this occurs and they have different software configurations).

It happens on more than the E1505/640m so I think its more of a manufacturing or software flaw on Dell's part.

---

