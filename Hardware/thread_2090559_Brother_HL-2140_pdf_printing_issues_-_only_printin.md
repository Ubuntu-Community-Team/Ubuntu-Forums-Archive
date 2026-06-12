---
title: "Brother HL-2140 pdf printing issues - only printing part"
date: 2012-12-02
forum: Hardware
---

### Post by Random_Pinenut_Joy on 2012-12-02
I've just bought an HL-2140 laser printer, so I can print off the LPIC manuals I need to study. My issue is that it is only print a part of the pdf file when asked to print off all the odd pages. Though the number of pages printed off is inconsistent. One time it will do 12 pages the next time, (leaving off from where the printing stopped), it will only print off say, 5 pages & then 'n'pages.
Anyone with an idea of how to solve this would be most appreciated.
I have installed the appropriate brother driver support through synaptic.

---

### Post by pdc on 2012-12-03
> 

........hmmmmmmmmmmmmmmmm.........

I just wonder what driver you have installed ......

.....if you copy and paste this command into a terminal, and copy and paste the result back.......it is asking what drivers you have installed.....

> [COLOR="Red"]sudo dpkg -l | grep Brother[/COLOR]

Brother supply excellent drivers:

a) for your HL-2140 one would go here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2140](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2140)

and as ubuntu uses debian, one would install the lpr first and then the cupswrapper

........or b) use the Brother installer

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

......we can guide you through either if needed but if you declare what drivers are installed at present..............

---

