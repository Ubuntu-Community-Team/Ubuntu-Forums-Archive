---
title: "Synaptic packet manager issue- LAME repository"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by ninja123 on 2009-03-05
Hi,


I have this easy peasy installed in my Eee Pc 1000.

I cant get any libraries installed via packet manager.

It simply doesnt work...nor does it show me any error.

I search a packet n it returns nothing...i use proxy to connect to the internet. I changed network settings and also the prefernces in synaptic packet manager..but to no use.


Also I want to download LAME(liblame3 and liblame3-dev) but I guess it is not a licensed  packet for ubuntu so i downloaded mediduntu also. however since my packet manager wouldnt anyway work I have no clue what to do.


PLease help me!!

---

### Post by bubwitmaingay on 2009-03-05
Try to use the TERMINAL for your installation. Packages are the hardest to install especially with the dependency issues. Follow this:

1. Go to: Applications > Accessories > Terminal
2. Click on: Terminal
3. You will see something like ```
mitch@mitch-desktop:~$ 
```
4. Type this: ```
sudo apt-get install lame
``` , then strike Enter
5. It will ask for your password, it is the one you use in the log-in. Remember that as you type your password, it will not show on the screen (not even an asterisk or dots) but just type it, then strike Enter 

Then it will download and fetch the necessary repositories and dependencies to install LAME. The terminal automatically install everything, but do not forget that should be connected to the Internet when doing this.

Hope that helps. 8)

---

