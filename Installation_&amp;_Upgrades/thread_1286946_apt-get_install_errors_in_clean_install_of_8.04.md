---
title: "apt-get install errors in clean install of 8.04"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by abainbridge on 2009-10-09
I've just installed 8.04 (on a freshly formatted partition). Mostly it went well. The main problem I now have is that whenever I try to install a new package, I get an error message. For example,

[FONT=Courier New]$ sudo apt-get install samba[/FONT]

Produces this:
[FONT=Courier New]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.8 is to be installed
E: Broken packages[/FONT]

Any ideas? apt-get update doesn't help.

---

### Post by kiridude on 2009-10-09
I would recommend installing 9.04 as a first step. Why would you want to install an outdated version?

---

### Post by abainbridge on 2009-10-09
Oh sorry, should have said. I installed 8.04 because the machine is ancient. A P2 300 with 512mb RAM. It was previously running Ubuntu 7 happily. It's just a data server, I don't need a GUI or any thing fancy.

---

### Post by kiridude on 2009-10-09
Did you try with Synaptic?

---

### Post by wojox on 2009-10-09
Try:

```
sudo aptitude install samba
```

---

### Post by abainbridge on 2009-10-09
Logged in over ssh, due to a shortage of VGA leads...

So, I know how to fix this problem. apt-get remove samba-common, followed by apt-get install samba, will do the job. My question is why this is happening in the first place. It happens with every package I try to install.

---

### Post by arrange on 2009-10-09
Is it a very fresh install? Have you already updated the apt database? ```
sudo apt-get update
```

---

### Post by abainbridge on 2009-10-09
Already did apt-get update.

---

### Post by abainbridge on 2009-10-09
> **wojox said:**
> Try:

```
sudo aptitude install samba
```

Hmm, seems like aptitude has become a standard tool since I last used Linux (3 years ago). Maybe this would solve my problem. Unfortunately, I've already done the apt-get remove trick to get samba to install. So I need to test another package. However, having previously said the problem occurs with every package I try to install, I can't find another one that fails now. Typical.

So thanks for your suggestion! I'll use apt-get until I next have a problem, then I'll test it. Seems like I should switch to using aptitude permanently then though.

---

### Post by oldos2er on 2009-10-09
Have you checked to see if all repositories are enabled? System, Administration, Software Sources.

---

### Post by abainbridge on 2009-10-09
> **oldos2er said:**
> Have you checked to see if all repositories are enabled? System, Administration, Software Sources.

Yes, I checked that as soon as I installed Ubuntu.

---

### Post by oldos2er on 2009-10-09
> **abainbridge said:**
> Yes, I checked that as soon as I installed Ubuntu.

 Hmm. Have you tried different servers?

---

