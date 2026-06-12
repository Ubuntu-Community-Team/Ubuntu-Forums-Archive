---
title: "help with update."
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by lozenges on 2009-05-17
Hi! i am fairly new to kubuntu.
i did sudo apt-get update on my kubuntu 9.04 and it informed me that i have 4 new updates, but when i clicked on the little update gear it only shows 1 update, i didn't read what it was, i just click apply changes... that was my mistake. i took it for granted that it would go flawlessly. but half way through the upgrade got cut off and i guess it registered it as upgraded when it clearly hasn't has the last time i checked it was only at 60% before cutting off. so my question is, is there a way for me to check what was the last file i tried upgrading so i would could delete it and re-upgrade it.. any other alternatives are welcome. thanks in advance!
i tried sudo apt-get update again and no updates available. sooo...i need help.

---

### Post by kpkeerthi on 2009-05-17
Run these commands in a terminal. If no error is reported, you should be OK. Post back the errors, if any.
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by lozenges on 2009-05-17
i did sudo apt-get clean and it asked my for my password which i typed it. then nothing happened. so i typed in for update and upgrade.. reports that there is nothing to upgrade. so i guess there issn't a problem. thanks!
i am new to linux, could you please tell me what does the clean command do?
thanks again!

---

