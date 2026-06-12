---
title: "Xircom SpringPort 10/100 56K"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by alex@billsboatbarn.com on 2005-05-31
I have a Xircom modem / lan card and the lan card part works, i'm not sure how to access the modem part, but if someone could help me out w/ that I would greatly appreciate it, it is PCMCIA.

Thanks,
Alex

---

### Post by consecratus on 2005-06-01
Good day mate,

Try using Minicom and configure your modem using minicom.

Minicom usually comes with most distros but since I am pretty new to debian(I am redhat guy by the way...[Ubuntu resides in my laptop where redhats resides in our company's server rooms..)I was pretty surprised not to find minicom in ubuntu.

Well, Go to the Synaptics and enable some universe repos.

Search for minicom and download it, fire up your terminal and type 'man minicom' to find more about it and how to use it.
Use info command and man command to get the full idea. This way you will NEVER forget about it.

See how you go.

---

### Post by alex@billsboatbarn.com on 2005-06-01
I would do that, but I don't have a net connection on the particular machine that is having the issues (hence the need for the modem to work)... so does anyone have anyother suggestions?  I have gotten wvdial to dial w/ the modem, but it isn't PPP or I can't figure out how to make it, so any other suggestions?

---

### Post by alex@billsboatbarn.com on 2005-06-02
Problem solved...
After much searching throught the forums, I found there was no way to autodetect the modem port very well.. however, after some trial and error, I managed to use wvdialconf to locate the correct port and shoved that into the Ubuntu Graphical Networking dehackey and i'm online now...
I am impressed...  Linux has grown up a lot since I first started toying with it... and now it has made both of my computers...  Thanks so much!

---

