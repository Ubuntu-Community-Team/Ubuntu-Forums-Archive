---
title: "Battery Efficiency - LessWatts.org"
date: 2013-02-08
forum: Hardware
---

### Post by MartianTek3 on 2013-02-08
Hello Ubuntians, 

Have any of you had a laptop? 

Intially you had Windows 7, the power save option was a life saver Amen? 

But after getting sick of BSODs and performance issues 

You went to greener pastures of Ubuntu 

You loved the OS, until you unplugged the AC Power cord 

Sadly Ubuntu doesn't offer integrated power efficiency 

The point in Win7 I could get 3:30 hours of battery life (48wh capacity)  

Now in Kubuntu 12.10 it is split in half to about an hour... 

To tackle this problem I found POWERTOP and laptop-mode-tools 

However these tools do not give me the results I need 

I visited [https://lesswatts.org/]("https://lesswatts.org/")

In the Downloads tab installing PowerTOP was a piece of cake 

Thank you for reading this far: 

:arrow:THE PROBLEM(finally) 
the website says I must patch my linux kernel 
" *[COLOR="RoyalBlue"]Below are the list of patches that are merged upstream. They migrate a few commonly used timers to use these new kernel APIs.[/COLOR]*"

How do I do this?

GIT is a compiler right? 

GOAL: I want to install all the patches and bring my battery performance back to its former \\:D/ glory

---

### Post by xianbei on 2013-02-08
a bit of an aside, but i found a marked improvement by installing jupiter

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

it does a good job of knowing when to go easy on the throttle...

---

