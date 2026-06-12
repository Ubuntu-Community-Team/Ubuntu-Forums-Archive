---
title: "Canon UFR drivers and 12.04 LTS"
date: 2012-07-09
forum: Hardware
---

### Post by che_bizarro on 2012-07-09
Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit  12.04 LTS install but this morning I finally cracked it and hope that by  sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor  denies the CUPS executables which the driver needs. Add to  /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!

---

### Post by johnnybegood on 2012-07-16
Thanks a lot! It did help, I was going nuts trying to find a solution. I did the symlink a bit different, though, following [these instructions]("https://bugs.launchpad.net/ubuntu/+bug/502920/comments/10"):

ln -s /usr/lib64/lib* /usr/lib/x86_64-linux-gnu/

Thanks again!

---

### Post by tolbunt5 on 2012-11-29
I am having the same problem. I tried everything to no avail. Can anyone help me in layman's terms? I'm still a newbie to Linux. I have Ubuntu 10.04.

---

### Post by pdc on 2012-11-30
perhaps tolbunt if you tell us just a little bit about things ..

....which Canon printer do you want to install .....

....you are using Ubuntu 10.04 and is your version 32bit or 64bit please?

---

### Post by MrGregLund on 2013-02-21
Thanks a million.  I'd been struggling for a while with that one.  If this helps any other searchers, here is the error I was getting:

Canon_iR-ADV_C2020_2030_UFR_II: File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory


Directions above solved the problem.

Note:  the command 'alien' should use the option '-d' instead of '-s' to create the .deb package instead of a folder.

---

### Post by neotrode on 2013-03-04
I think I solved the mystery!  Like everyone else, I was going nuts!!!!
What's missing in che_bizarro's steps is the following:
Symlink these two files from the 64bit library to the standard library...

ln -s /usr/lib64/cups/backend/cnusb /usr/lib/cups/backend/cnusb
ln -s /usr/lib64/cups/filter/pstoufr2cpca /usr/lib/cups/filter/pstoufr2cpca

THEN... Restart your cups server...

sudo service cups restart

---

