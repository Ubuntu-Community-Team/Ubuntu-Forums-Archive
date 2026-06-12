---
title: "[SOLVED] Problem with update manager and other apps."
date: 2008-08-10
forum: General Help
---

### Post by Unholy_goat on 2008-08-10
I opened the update manager yesterday to install the update i entered my password and it came up with this response: 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/epiphany-browser/epiphany-browser-data_2.22.2-0ubuntu0.8.04.5_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/epiphany-browser/epiphany-browser-data_2.22.2-0ubuntu0.8.04.5_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused) 

for each different update, the add/remove programs and synaptic both give me a similar message 

sorry for dragging it out but google earth cannot connect to it's server either

any help would be appreciated 
thanks in advance

---

### Post by gobbles414 on 2008-08-10
> **Unholy_goat said:**
> I opened the update manager yesterday to install the update i entered my password and it came up with this response: 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/epiphany-browser/epiphany-browser-data_2.22.2-0ubuntu0.8.04.5_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/epiphany-browser/epiphany-browser-data_2.22.2-0ubuntu0.8.04.5_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused) 

for each different update, the add/remove programs and synaptic both give me a similar message 

sorry for dragging it out but google earth cannot connect to it's server either

any help would be appreciated 
thanks in advance At what time of day were you trying to access the system updates and Google Earth? IT professionals typically do server maintenance in the very early morning hours -- at like 2:00 AM.

---

### Post by Unholy_goat on 2008-08-11
it still says the same message i tried to search a location in case it was just an error and it says:

HTTP 400(Bad Request) The request could not be understood by the server due to malformed syntax.

---

### Post by Unholy_goat on 2008-08-11
I'm able to install the updates manually by copy and pasting the Url in the error message into my browser if that helps anyone
Thanks

---

### Post by gobbles414 on 2008-08-14
Please post a screenshot of your each tab in your *System => Administration => Software Sources*; this means five screenshots total.

---

### Post by Unholy_goat on 2008-08-19
sorry about the delay i went on holiday for the weekend,

[IMG]http://a561.ac-images.myspacecdn.com/images01/7/l_c2c6104be03c110deec65c691fd24560.png[/IMG]

---

### Post by Unholy_goat on 2008-08-19
[IMG]http://a327.ac-images.myspacecdn.com/images01/69/l_3f8753f5e038f4c01f9b960fa0b08c96.png[/IMG]

---

### Post by Unholy_goat on 2008-08-19
[IMG]http://a403.ac-images.myspacecdn.com/images01/87/l_f19d771e6e138d7f21935011624cb0b2.png[/IMG]

---

### Post by gobbles414 on 2008-08-19
Please post another screenshot of the *Ubuntu Software* tab, Unholy_goat. Your current screenshot of that tab is partially blocked by another window.

---

### Post by Unholy_goat on 2008-08-20
Sorry about that

 [IMG]http://a793.ac-images.myspacecdn.com/images01/84/l_1b63af7a663445f588ce860a04f41fd0.png[/IMG]

---

### Post by gobbles414 on 2008-08-21
Alright Unholy_goat, your *Ubuntu Software* and *Third Party Software* tabs both look strange to me. I've attached screenshots of those two tabs from my Ubuntu 8.04 (32-bit) computer, for your reference.

Which version of Ubuntu are you using? You're not using an Ubuntu branch are you, like gOS? Did you install Ubuntu with a LiveCD? Or, did you install using an "alternate CD" instead? Also, have you done a lot of customization to your *Software Sources*?

---

### Post by Unholy_goat on 2008-08-22
I'm using 8.04 LTS on 32bit comp , i installed it through the update manager, but originally installed 7.10 from a live cd, and i've not done any customisation as far as sofware sources go.

---

### Post by gobbles414 on 2008-08-22
> **Unholy_goat said:**
> I'm using 8.04 LTS on 32bit comp , i installed it through the update manager, but originally installed 7.10 from a live cd, and i've not done any customisation as far as sofware sources go. I think that I've discovered the solution to your problem!

Several strange aspects of the screenshots you provided can be explained by the fact that you upgraded from 7.10 to 8.04. It only takes a few moments of searching in these forums to discover just how many problems upgrading from one version of Ubuntu to another can cause, and I know from personal experience how destroyed a system can get during the upgrade process. I've argued and will continue to argue that the upgrade feature in Ubuntu may sound like a good idea because it's so convenient, but that it's extremely unreliable in the real world.

IMHO, the easiest/quickest/best solution to your problem is for you to backup your data, reformat your hard drive, and install Ubuntu 8.04.1 from a Ubuntu 8.04.1 LiveCD. Downloading a new LiveCD shouldn't take too much longer than downloading the upgrade in Update Manager, but it should yield much better results.

PS: People have also experienced problems when upgrading from one version of Windows to the next. So, this isn't just a Ubuntu problem. IMHO, the very concept of upgrading without reformatting is fundamentally flawed.

---

### Post by Unholy_goat on 2008-08-23
ok thanks for the advice, i'll get doing that now

---

### Post by gobbles414 on 2008-08-23
> **Unholy_goat said:**
> ok thanks for the advice, i'll get doing that now Please feel free to ask any questions that you may have about the reinstallation process. And of course, let us know if my recommendation solves your problem.

---

### Post by Unholy_goat on 2008-08-25
I've reinstalled with the live cd and everything is working better than it was before, thanks for the advice :)

---

### Post by gobbles414 on 2008-08-25
> **Unholy_goat said:**
> I've reinstalled with the live cd and everything is working better than it was before, thanks for the advice :) That's what I thought would happen.:) If this solution continues to work during the next few days, I'd recommend that you go ahead and mark this thread as SOLVED. Thanks...

---

### Post by Michl on 2008-09-11
Reinstallation might solve the problem but his
problem was not due to upgrading from 7.10.  I
did a fresh install of 8.04 from a live cd and
suddenly I have the very same problem.  I don't 
know why this happened suddenly, but it is the
same problem.  There is another thread with a
different less drastic set of solutions.  You
can fix a leaky roof by tearing the house down
and building a new one or by fixing the leaky
roof.

He probably just installed anon-proxy by mistake
and removing it takes care of the problem.  You
can remove it with 

```
sudo apt-get --purge remove anon-proxy
```

or by reinstalling ubuntu ... or by buy getting a
new computer...

By the way, since port 4001 was the problem, you can
check what was using that port as follows:

```
sudo grep -r 4001 /etc
```

---

