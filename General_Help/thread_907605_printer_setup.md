---
title: "printer setup"
date: 2008-09-01
forum: General Help
---

### Post by valladaresj on 2008-09-01
Does anyone know which driver to use for an HP Deskjet D2560. I've tried everything but I can't get this thing working.

---

### Post by wolfen69 on 2008-09-01
go to synaptic and make sure the following are installed: hpijs, hplip, hplip-data, and hplip-gui. most hp printers will "just work" with no configuration.

---

### Post by wolfen69 on 2008-09-01
also, on [this]("http://hplip.sourceforge.net/models/deskjet/deskjet_d2500_series.html") page, it says your model should work fine.

---

### Post by nikgare on 2008-09-01
This page [http://hplip.sourceforge.net/models/deskjet/deskjet_d2500_series.html](http://hplip.sourceforge.net/models/deskjet/deskjet_d2500_series.html) says that you need hplip 2.8.5 or later.

---

### Post by fballem on 2008-09-01
The version that is currently in the Repository is 2.8.2, which won't support your printer. Here's how you install the latest version of HPLIP (currently 2.8.7)

[LIST=1]
[*]If you have any version of HPLIP currently installed, you should remove it completely. To do this:
[LIST=2]
[*]Open Synaptic (System | Administration | Synaptic Package Manager) and search for 'hplip'.
[*]If hplip is installed, then Right-Click and select 'Mark for complete removal'. You will get a list of items that will also be removed, which is acceptable - anything that you remove that's actually needed will be reinstalled in a moment. Select OK.
[/LIST]
[*]Close Synaptic.
[*]Open Firefox and go to the following link: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
[*]Download the Automatic Installer. Save it to your desktop.
[*]Close Firefox.
[*]Open a Terminal, and type the following commands (you may copy and paste). Do not put 'sudo' in front of either of these commands - the installer will ask you for your password during the installation process.
```
cd ~/Desktop
sh hplip-2.8.7.run

```
[*]This will open up your installer. You didn't indicate whether your printer is USB or Network. If you select the Automatic installation option, and carefully read the prompts, then you shouldn't have a problem. Note that it will install all of the dependencies that you require.
[*]You'll know the printer is working if the test page prints.
[/LIST]

Hope this helps,

---

### Post by marcelo danico on 2008-09-01
I have a similar problem as the OP--I need the latest HPLIP.  But can't manually install because it hangs due to not getting python-dev.

Python2.5-dev seems to be impossible to install using Synaptic.

Any suggestions?

This is what I get in the terminal after sudo apt-get install python2.5-dev

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.2-2ubuntu4.1) but 2.5.2-2ubuntu5 is to be installed
E: Broken packages


---

### Post by fballem on 2008-09-01
> **marcelo danico said:**
> I have a similar problem as the OP--I need the latest HPLIP.  But can't manually install because it hangs due to not getting python-dev.

Python2.5-dev seems to be impossible to install using Synaptic.

Any suggestions?

This is what I get in the terminal after sudo apt-get install python2.5-dev

Open a Terminal an try the following command:

```
sudo apt-get -u upgrade
```

That should update your packages, including hopefully Python. It will give you a list of the packages that will be updated and ask you if you want to proceed (y/n). If it's okay, then answer y

If that doesn't work, then try

```
sudo apt-get install python2.5
```

If neither of those work, then hopefully someone else can help, since you've just exhausted my knowledge.

---

### Post by marcelo danico on 2008-09-01
Thanks.

I actually got the new manual install to work by following instructions from here -->[https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/244110](https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/244110)

 > shadtor wrote on 2008-07-03: (permalink)

Found way to install python2.5-dev - downloaded package from

[https://launchpad.net/ubuntu/hardy/i386/python2.5-dev/2.5.2-2ubuntu5](https://launchpad.net/ubuntu/hardy/i386/python2.5-dev/2.5.2-2ubuntu5)

ran the .deb file and installed.....


So far HPLIP runs on startup but printer has an error. Running printer configuration now.

Should I be using Foomatic instead of Gnome Cups?

---

### Post by marcelo danico on 2008-09-01
Issue resolved.  Foomatic works fine. But running printer config (from system--administration--printing) and finding the "new" correct driver was the solution.

---

