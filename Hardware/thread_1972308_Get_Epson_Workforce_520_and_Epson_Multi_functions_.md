---
title: "Get Epson Workforce 520 and Epson Multi functions scanning in Ubuntu with Iscan"
date: 2012-05-03
forum: Hardware
---

### Post by tdlam on 2012-05-03
If you have spent many hours like I have hunting down a way to scan from your Epson All In One mutli function unit then here's a site that has turned out to be a life saver. For me I was never able to get my EPSON WORKFORCE 520 working as a scanner. But I stumbled on this site which was in a link I saw in a post in a forum somewhere.(could have been a UBUNTU forum dunno so if this info is a repeat  I apologize!) I had checked out so many forums for getting my EPSON WORKFORCE 520 scanning in Xubuntu. (But the site lets you choose UBUNTU not XUBUNTU so I left the thread header UBUNTU) that I can't remember for the life of me where I saw it....anyway...here's the site:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo)

Top of the page is the printer driver. I already have this unit PRINTING ok so I didnt need that. I was looking to get it to scan. The middle of the page is legal stuff. I ignored this. There are all the liscence agreements  and the "check OS" pdfs...but by all means if you need to check em out. At the lower third of the page is the links you need to set up Iscan. Here  you can choose the model of your unit ( I chose epson workforce 520) then at bottom of the page you choose

*Distribution* (UBUNTU)

and 

*Distribution version* (I chose 11.10 even though I just installed the latest long term release and it works just fine)

Then click "next".

The next page has the printer driver for your unit and the deb packages for setting up Iscan to get the unit scanning.
*Now this is important* 
BEFORE you do ANYTHING go to the very bottom of the page and download the manual for Iscan...its a pdf file and read the instructions on Page 1 and page 4. 
Page 4 is critical because if you DON’T install the packages in this order Iscan won’t work (at least for me it didn’t).

I already had SANE installed so didn’t need to worry about page 1. (But being a linux noob I can't remember just how I did that or if it is bundled with Xubuntu.) Once I installed all the packages in the order specified, ( I right clicked on them and chose to have UBUNTU software center install them for me) Iscan was ready to use and saw my EPSON WORKFORCE 520 multi function just fine. I am now scanning with it in Xubuntu.

Understand folks...I am a linux noob. This post is just my retelling of how I got this to work. I can't trouble shoot if you folks find any issues. Heck, I am counting my blessings that the printer scanner is working at ALL!
Folks here have been very generous with helping me and this post is just my small way of trying to give back for the help I have received. 
Anyway, I hope this makes someone's life a bit easier and all the best to you all!

---

### Post by mips on 2012-05-03
> **tdlam said:**
> 
I already had SANE installed so didn’t need to worry about page 1. (But being a linux noob I can't remember just how I did that or if it is bundled with Xubuntu.)

Yes it's bundled with Xubuntu.

---

### Post by tdlam on 2012-05-03
Thats good to know thanks for the info. All the best to you.

---

### Post by LaJuan on 2012-06-12
Hi TDLam,

just wanted to say thanks for the info!!!!!!! I'm running 12.04 on my Dell Precision 370 with 4GB RAM, and two 400HDD. I used the info you provided and now my printer is back on track!!!!!!

Thanks again,

LaJuan
:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by tdlam on 2012-06-29
Thats great news. If this info is able to help at least one person its worth it...because it was a BEAR trying to get this printer to work...all the best!

---

