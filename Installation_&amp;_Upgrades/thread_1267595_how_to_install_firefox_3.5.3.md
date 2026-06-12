---
title: "how to install firefox 3.5.3 ?"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by tonjaa on 2009-09-15
[COLOR=RoyalBlue]ubuntu9.04 
i download firefox 3.5.3 save on desktop filename firefox3.5.3.tar.bz2
how to use command to install it ? please guide me by step[/COLOR] :confused:

---

### Post by zvacet on 2009-09-16
First  put it in home directory.Then type in terminal

```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

Hit enter and that's it.

---

### Post by tonjaa on 2009-09-16
[COLOR=YellowGreen]thank you very much.[/COLOR]

---

### Post by lukeiamyourfather on 2009-09-16
I would suggest not doing that. Firefox 3.5 is already in the repositories and gets updated through the package manager when there's a new version. I think it shows up as Shiretoko which is Firefox without the branding.

```
sudo apt-get install firefox-3.5
```

No point in reinventing the wheel and dealing with manually updating the software. Cheers!

---

### Post by TheStroj on 2009-09-16
You can also type Firefox in Google and download the latest package, then unpack it somewhere and double-click a file named "firefox" and you're using firefox 3.5 =). Too simple ^^

---

### Post by bryce4president on 2009-09-16
luckyiamyourfather,
I tried that and it didn't work.  It said it couldn't find firefox-3.5.  Is it in the Universe repository?  I haven't seen it.

---

### Post by prakreet on 2009-09-16
firefox 3.5 is not in ubuntu repos. [strange]... the version they have there is 3.0.14. i don't know why ubuntu doesn't update this most used software...

like wise they don't have vlc 1.0 in their repos. only the previous 0.9.x series. what is happening to ubuntu... repos are very much outdated...

---

### Post by zvacet on 2009-09-17
New packages comes with new releases.I think it is because of stability of system.Correct me if I'm wrong.

---

