---
title: "Shuts down but doesn't power off?"
date: 2012-02-12
forum: Hardware
---

### Post by Hamani on 2012-02-12
Hey guys, 

Strange one here ... 

My PC will shut down (as far as the purple Ubuntu screen) then just stops and doesn't actually power down. 

Any ideas? 

I'm running Ubuntu 11.10 on Dell Optiplex 755. 

- Gary. 

p.s. While I'm here, I figure I may as well mention this too: When I'm playing a video (say on youtube or 4oD) and click to make it 'full screen' it doesnt actually full screen, just blanks out the surrounding screen and makes it a 'little' bigger. How do I make it fill the entire screen?

---

### Post by duncang92 on 2012-02-12
You could try following the info in this link

[http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/](http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/)

I have the same problem and found this which seems to have worked for a lot of people but unfortunately not me.

---

### Post by Hamani on 2012-02-12
Hey Duncan, 

That worked great for fixing the shutdown problem. Many thanks. 

Any idea's for fixing the full screen problem?

---

### Post by winh8r on 2012-02-12
For anyone who cannot find a solution to improper shutdowns using the gui then a simple way to do it is

open a terminal

type

sudo shutdown -h now

hit enter

enter your password when asked and hit enter

Your computer will now shutdown fully


You can also use the command to restart your computer by using


sudo shutdown -r now

give it a try 

it gets you used to using the terminal too!

---

