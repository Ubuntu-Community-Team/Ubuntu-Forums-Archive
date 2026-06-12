---
title: "Printer problems,  used to work fine, now won't print from Ubuntu"
date: 2019-12-19
forum: Hardware
---

### Post by dave1662 on 2019-12-19
I am running Ubuntu 16.---- sorry I don't remember the rest of the numbers.
My laptop is a HP Pavilion dv7
My printer is a Canon MG8120B

My system used to work great, I could print anything I wanted. My printer's USB cable is plugged directly in to my laptop. My wife uses the printer by WiFi

Then things started to get weird a few months ago.  I could not print from a web page once in a while, then it got to the point I couldn't print form any web page, yet I could print from Libre Office Writer any time I wanted. I could also print from Draft Sight.

Now I am getting to the point I can't print anything. The office writer won't print, and the Draft Sight program worked great in October (thank fully) but it won't print now

The strange thing I noticed is,  When I send something to the printer the screen on it lights up and IF it makes a slight click sound the printer will work,  IF it does not make the click sound the printer will not work.
The screen on the printer says it is printing from the PC, and after a while it says it is done printing. Same thing on the laptop, the print que shows everything is fine. I might be able to print 1 out of 50 attempts.

If I fire up my laptop on windows it works fine.

Yet all the time I am having problems my wife has no problem

There are no Linux drivers for my printer.

What is going on??

---

### Post by mörgæs on 2019-12-20
Drivers for a closely related model are [here]("https://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg8140.html?type=drivers&language=en&os=linux%20(64-bit)").

Another option is finding the drivers through a [PPA]("https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz?field.series_filter=").

---

### Post by brian_p on 2019-12-21
> There are no Linux drivers for my printer.

But your wife can print!

---

### Post by kurt18947 on 2019-12-22
I have no experience with Canon & Linux but here's something to consider:

[https://asia.canon/en/support/0100924010/8](https://asia.canon/en/support/0100924010/8)
[B][SIZE=5][B]UFR II/UFRII LT Printer Driver for Linux V5.00
[/B][/SIZE][/B]

This might be too new if your Ubuntu 18.04 uses the 4.15 kernel but a bit of time on canon Asia may find something suitable. If you're in doubt about which kernel you're using, open a terminal and type

```
uname -a
```

You should get something that looks like this:

```
**5.0.0-37-generic #40~18.04.1-Ubuntu SMP **Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by yancek on 2019-12-22
If it worked before an still works from another computer, it is not likely to be a hardware issue.  Have you tried accessing the printer configuration in CUPS?  In a browser just enter:  localhost:631 and click the Administration tab in the upper left.  The new screen should show options on the right of the page including error and access log info.  If you click on the Printers tab at the top, the new windows should show the name of your printer as well as the status, idle/ready.

---

### Post by brian_p on 2019-12-22
> **brian_p said:**
> But your wife can print!

That wasn't an idle remark. We are left to guess whether your wife is using Linux.

If not, it is of no relevance to your problem.

---

