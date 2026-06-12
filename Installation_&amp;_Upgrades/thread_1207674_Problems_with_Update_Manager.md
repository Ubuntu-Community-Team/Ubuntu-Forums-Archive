---
title: "Problems with Update Manager"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Anteyra on 2009-07-08
I am getting the following error message when starting Synaptic Package Manager

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.



Can anyone help me, please?

---

### Post by jenkinbr on 2009-07-09
Open a terminal (Apps => Accsessories => Terminal) and run

```
sudo apt-get update
```

If it posts errors, copy and paste the output inside [noparse]```

```[/noparse] tags.

---

### Post by Soul-Sing on 2009-07-09
```
sudo cd /var/lib/apt/lists/
```
```
sudo rm archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Anteyra on 2009-07-09
I ran the terminal and these are the errors that I got: 
```

Reading Package Lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_  binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by raymondh on 2009-07-09
Did you run the codes in post # 3?

---

### Post by Anteyra on 2009-07-19
Thanks for the help guys, my dad managed to figure out what was wrong.

The file was not actually there.... when the update was being done it looked like at the moment that particular file [FONT=monospace][/FONT]was being done the hub disconnected for a few seconds so the internet error page text was put in instead of the actual file being recorded.

So I had to use my dad's copy of the correct file and delete the file that was wrong, and now I can use the Update Manager and Synaptic.

---

### Post by genfinch on 2009-10-25
Thank you people on ubuntuforums!!! you are worth your weight in gold!

---

