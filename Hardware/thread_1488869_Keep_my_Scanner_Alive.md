---
title: "Keep my Scanner Alive"
date: 2010-05-20
forum: Hardware
---

### Post by nolo on 2010-05-20
I'm sure that after I post this, someone will post a more elegant solution to this problem.  Cool!  But I have always made do with what I know.  The problem: after upgrading to Karmic from Jaunty, my scanner (Epson GT-2500) became unreachable by gscan2pdf or xsane after it had been idle for some time.  I tried lsusb, scanimage -L, and scanadf -L to wake it up with verying degrees of success.  I even wrote a script that ran lsusb and scanadf -L first before starting gscan2pdf.  Seemed better at first but eventually it became obvious I hadn't made any real headway.  I was getting tired of having to get up and cycle the power on my scanner.  So I spent some time googling "keepalive scanner karmic" but didn't come up with anything helpful.  So I says to m'self "How do I send inquiries at a regular interval to keep my scanner alive?"

I decided that must be what they invented cron for so I made this little crontab entry:

> # m h  dom mon dow   command
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /usr/bin/scanadf -L
Now my scanning apps find the scanner immediately and I'm a happy camper.  

Hopes this helps anybody suffering the indignities of sleepy scanners.

Nolo

---

### Post by tgalati4 on 2010-05-20
Rather than run the scanner wake 24/7, why not make a desktop launcher that applies the wakeup script.  Name it "Wake Up Scanner".  Choose a suitable icon for it:

locate icon

Then you just double-click on the launcher before you want to use the scanner.

If you leave the scanner awake all the time, wouldn't that shorten the lamp life?

---

### Post by nolo on 2010-05-21
I tried that, the problem is I have yet to come up with a reliable wake up script.  lsusb, scanadf -L, and scanimage -L won't reliably wake up the scanner once it's asleep. Keeping it awake is the only reliable solution I've come up with so far.  If somebody knows an initialization string that wakes up Epson scanners, I could put it either in a wake up script or a start up script.  You're probably right about the scanner lamp, but I'm hoping that a Lucid upgrade will fix the problem.  Just gotta do it when I have time to re-install Hylafax, and hold my mouth just right to make my windmodem work with it (the most time consuming part of every upgrade so far).  I welcome any suggestions, since, as I said from the beginning, I'm sure there is a better way to do this.

Thanks for the input,

Nolo

---

