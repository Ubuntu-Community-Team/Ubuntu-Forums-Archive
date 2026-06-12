---
title: "How to automatically execute command after some package has been updated?"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2009-04-17
Hi,
is there any way that some command is executed after package is upgraded?

Example:
1. I have installed KolourPaint:
sudo apt-get install kolourpaint

2. Then I have installed packages from Synaptic (to get Slovenian language support for KolourPaint):
kde-l10n-sl
language-pack-kde-sl
language-pack-kde-sl-base packages

3. Because this translation for KolourPaint in above packages is not completed I have downloaded new fully translated .mo translation file from (.mo file is one of the files inside above packages):
[https://translations.launchpad.net/ubuntu/jaunty/+source/kdegraphics/+pots/kolourpaint/sl/+export](https://translations.launchpad.net/ubuntu/jaunty/+source/kdegraphics/+pots/kolourpaint/sl/+export)

4. I replaced existing file with downloaded file using command:
sudo mv sl_LC_MESSAGES_kolourpaint.mo /usr/share/locale-langpack/sl/LC_MESSAGES/kolourpaint.mo

5. The main problem is that translation package for KolourPaint on Ubuntu 8.10 is not completely translated (more then 100 strings missing), but KolourPaint on Jaunty has full translation, so I use translation .mo file from Jaunty and copy it on Ubuntu 8.10. I know it is strange, but new translation file solves translation problem.

6. Now every time when packages from step 2 are upgraded using System | Administration | Update Manager I have to manually replace translation file (step 4).

Question: is there any way I could automatically run script if one of the packages form step 2 upgrades?

I know I can lock package in Synaptic to stop updating, but I would like to update package if available (to get new translation for other programs), just after upgrade I would like to have existing Jaunty translation version of KolourPaint.

Regards

---

