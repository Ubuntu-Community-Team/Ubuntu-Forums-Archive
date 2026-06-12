---
title: "Keyboard configuration resets after restart"
date: 2011-01-09
forum: Hardware
---

### Post by rsmallri on 2011-01-09
I am having an issue with ubuntu that is driving me slowly mad. When I start the machine there are two keyboard configurations, USA and USA with dead keys, with the latter selected by default. When using punctuation marks I have to hit them twice otherwise they modify the letter I press next. To fix this I simply have to delete the USA with dead keys configuration. However, every time I restart the machine it is back.

Does anyone know why this might be happening? What is the configuration file that ubuntu loads for the keyboard? I am thinking maybe my user doesn't have permission to edit the config file and that is why the changes don't persist past restart. There were some other threads on here with a similar issue however in all of those cases I saw the fix was to make changes to some offending lines in the /etc/X11/xorg.conf. My xorg.conf however does not have a section for the keyboard. 

Any ideas? I am running Ubuntu 10.10

---

