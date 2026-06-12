---
title: "Modem working at one location, not at another"
date: 2008-07-17
forum: General Help
---

### Post by CyberChunk on 2008-07-17
Hello all, I've got a strange problem.

I'm using Ubuntu 7.10 on a 5 old Toshiba Satellite laptop. I've downloaded and installed drivers from this site:
[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/]("http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/")
I use wvdial or kppp to connect to the internet.

My dialup modem works great at home, but not at my summer home, which is about 20 miles away. The dialup number is good for both areas, and I have no problem connecting with my Windows laptop at both places. My Ubuntu laptop will only work at home.

I get a 'no carrier' error when I try to connect from the summer home. I've tried changing many of the adjustable settings in kppp (such as modem speed) with no luck.

The modem initializes, dials the number and then returns the 'no carrier' error after a minute or so. I am able to call my home phone from my summer home and when the phone is picked up the modem returns a line busy error. I've tried using dialup numbers for different areas for my ISP, and still no luck.

Any help would be appreciated.

---

### Post by CyberChunk on 2008-07-19
I've also tried connecting at a neighbour’s house yesterday while I was at my summer house, and I received the same no carrier error.

---

### Post by editrix on 2008-07-20
It looks like the problem is with the phone line, not the modem or the setup.  Have you contacted the phone company?

---

### Post by CyberChunk on 2008-07-22
I've called the phone company, and the equipment that is in the country is antiquated. The equipment in town is more modern.

It's still weird how Windows will work in the country while Ubuntu doesn't. However, I'm going to try a USB Robotics 5633 modem. I found some drivers that I am going to try with it and hopefully that will fix the problem.

If it works, I'll be going 100% Linux. I tired of being nickel and dimed by Microsoft.

Thanks for the reply and your help.

---

### Post by ModelM on 2008-07-23
Please post the contents of your /etc/wvdial.conf file here. I only speak wvdial, so anything from KPPP would not be understood.

It sounds like the init string in windows is different than in wvdial. That would explain why Windows can connect but not Ubuntu.

So, let's have a look at exactly what instructions wvdial is giving your modem...

---

