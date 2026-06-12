---
title: "radeon hd 8870m"
date: 2014-02-19
forum: Hardware
---

### Post by Juvencio on 2014-02-19
Good day to all

I am busy trying to set-up a Dell inspiron 17 laptop for a friend, with Ubuntu 30.10 64 bit.
This issue that I am having is the AMD radeon hd 8870m card.

I have tried all the drivers listed by Ubuntu by default, and the ones compiled by AMD but it keeps braking the installation.

The screen by default is low res and over saturated with green so everything is shades of green.

---

### Post by Mark Phelps on 2014-02-19
I recently acquired an AMD 8850 and none of the Repository drivers installed properly.

What DID work was the following:
1) Download the appropriate Catalyst 14.1 beta Linux file from the AMD drivers site
2) Extract the "run" file from the archive
3) Make the "run" file executrable by doing > sudo chmod +x <filename>
4) Copy the file to a local directory under $Home
5) Execute the .run file and choose the option to install it.

---

### Post by soum_axetuirk on 2014-02-20
first of all correct your question.Ubuntu 13.10...(not 30.10)
for graphics driver to work correctly use this command at terminal.it will install your graphics driver.

```
sudo apt-get install fglrx fglrx-pxpress
```

---

### Post by Juvencio on 2014-02-21
Thanks Mark Phelps for the reply. I fixed the issue with fglrx Drivers. If they do come back with an issue i'll try what you suggested.

Also Thanks soum_axetuirk I already did use the fglrx Drivers, but it doesn&#8217;t work on 13.10. Seems to clash with unity (and thanks for the note for 30.10, typing to fast) but to solve the issue I downgraded to 12.04 LTS (fglrx Drivers are only supported up to 12.10)

As the Radeon hd 8870m card is so new, I think the issue will be solved on the next release 14.04 LTS.

Also just as a note. (I cant fix it now, as I had to return the laptop) For some resin if I boot in to Ubuntu, the drivers are not detected. But if I boot to recovery mode, then resume normal boot it detects the drivers. Also to boot to windows 8.1, you first need to boot to Ubuntu (not recovery mode) you don&#8217;t need to log in just restart, then it will boot into windows.

If I had a weekend, I could of sorted it all out. I don&#8217;t know why people get hardware then hope it works out the box. Maybe I should start asking a fee for fixing PC&#8217;s. But that&#8217;s my problem.

[More in info on fglrx drivers.]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD")

---

### Post by Mark Phelps on 2014-02-21
> As the Radeon hd 8870m card is so new, I think the issue will be solved on the next release 14.04 LTS.

Perhaps ... but I'm using an HD 8850 and it works with the AMD Beta 14.1 drivers.  Since the drivers work with all the HD 8x-series, I would think they would work with yours as well.

I would advise AGAINST using drivers from the repos, as all my attempts to use them have resulted in a corrupted system.

---

### Post by Juvencio on 2014-02-21
Will keep it in mind, just hope that laptop works until the next Ubuntu release.
I hate working with a time limit. I also do need sleep some times.

But thanks again for the reply.

---

