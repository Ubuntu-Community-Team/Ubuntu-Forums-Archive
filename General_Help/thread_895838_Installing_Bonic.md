---
title: "Installing Bonic"
date: 2008-08-20
forum: General Help
---

### Post by Randomness6454564 on 2008-08-20
I have the .sh file that I downloaded from the bonic website and I have no idea what to do with it. I know virtually nothing about linux. Especially the command line. It might as well be in Mandarin Chinese.

---

### Post by ilovelinux33467 on 2008-08-20
This is how you install .sh files in linux

Do this in terminal
```
sudo /path/to/shfile.sh
```

---

### Post by oldos2er on 2008-08-20
> **Randomness6454564 said:**
> I have the .sh file that I downloaded from the bonic website and I have no idea what to do with it. I know virtually nothing about linux. Especially the command line. It might as well be in Mandarin Chinese.

 Do you mean Boinc? It's on the repositories; the packages you want are boinc-client and boinc-manager.

---

### Post by Randomness6454564 on 2008-08-20
It's one of the linux ones on this page [http://boinc.berkeley.edu/download_all.php](http://boinc.berkeley.edu/download_all.php)

> sudo /path/to/shfile.sh

Do I literally type "path" and "do"? I assumed not and typed my name and then "desktop". It didn't seem to work. The name of the .sh is "boinc_6.2.15_i686-pc-linux-gnu.sh" which is a lot, can I just rename it "bonic.sh"?

---

### Post by oldos2er on 2008-08-21
> **Randomness6454564 said:**
> It's one of the linux ones on this page [http://boinc.berkeley.edu/download_all.php](http://boinc.berkeley.edu/download_all.php)



Do I literally type "path" and "do"? I assumed not and typed my name and then "desktop". It didn't seem to work. The name of the .sh is "boinc_6.2.15_i686-pc-linux-gnu.sh" which is a lot, can I just rename it "bonic.sh"?

 Again, this is much easier to install from the repositories. But if you're determined to do it this way, open a terminal, type "cd Desktop" then "sh ./boinc_6.2.15_i686-pc-linux-gnu.sh"

 Use the Tab key for filename completion. And remember Linux is case-sensitive; it's 'Desktop', not 'desktop'.

---

### Post by Randomness6454564 on 2008-08-21
Actually I don't even know what a repository is. But I should learn it the hard way anyway.

"open a terminal, type "cd Desktop" then "sh ./boinc_6.2.15_i686-pc-linux-gnu.sh""
didn't work. what are repositories?

---

### Post by susanmiller on 2008-08-21
Hi
I like your posting.
[URL="http://www.drugtreatments.com/washington"]
 Washington Drug Treatment[/URL]

---

### Post by jotacebusta on 2008-08-21
The easiest way to install programs is via Synaptic:

go to System -> Administration , and you'll find it there.
Look for "boinc", and you should get at least boinc-client, and boinc-manager. Check them and click on "apply". That's it.

---

### Post by oldos2er on 2008-08-21
> **Randomness6454564 said:**
> Actually I don't even know what a repository is. But I should learn it the hard way anyway.

"open a terminal, type "cd Desktop" then "sh ./boinc_6.2.15_i686-pc-linux-gnu.sh""
didn't work. what are repositories?

 What exactly didn't work?

 As for repositories, see [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by Landier on 2008-08-28
you can find kinda quick install guide here : [http://boinc.berkeley.edu/wiki/Installing_on_Linux](http://boinc.berkeley.edu/wiki/Installing_on_Linux)

working on Ubuntu 8.04 - Hardy Heron

---

### Post by nixie21 on 2008-09-09
Anyone know why the repositories have the old version?

thanks!

---

### Post by oldos2er on 2008-09-09
> **nixie21 said:**
> Anyone know why the repositories have the old version?

thanks!

 Because they are only updated every six months.

---

### Post by egwest on 2008-09-13
been a lot longer then 6 months for Bonic, the one in the repositories is 5.10.45 and the newest one is  6.2.15. Anyone know how to manually upgrade it?

---

### Post by oldos2er on 2008-09-14
Go to [http://setiathome.ssl.berkeley.edu/](http://setiathome.ssl.berkeley.edu/) and download it.

---

### Post by bonfire89 on 2008-12-19
setting up and running this from ubuntu server is very confusing and the documentation is terrible.

I have installed boinc-manager boinc-client  but, have not gotten much further than that. :(

---

### Post by njdube on 2008-12-22
I've installed boinc from the repo.  How do I get the boinc client to start on boot with out the boinc manager starting up in the system tray when I log on?

---

### Post by Kevbert on 2008-12-22
Best way to install Boinc is via the command line with
```
sudo apt-get update
sudo apt-get install boinc-client boinc-manager
```
If you use Synaptic you may have problems attaching a project.

---

