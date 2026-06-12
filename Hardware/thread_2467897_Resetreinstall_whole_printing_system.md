---
title: "Reset/reinstall whole printing system"
date: 2021-10-11
forum: Hardware
---

### Post by knahrvorn on 2021-10-11
A while ago I had some problems printing, and at the time I thought it was caused by settings and/or drivers, when in reality it was the printer itself. I basically made things much worse trying to fix what was not broken, including installing and removing packages and installing non-deb HP printer drivers. Now I find myself able to add a printer that I connect, but unable to print to said printer (nothing happens, print job stays in queue indefinitely -- for both my HP and Brother printers).

What I would really like to do is basically start over, because I know both my printers work flawlessly on other Ubuntu computers just by plugging them in. Is there a way (apt command perhaps?) that I can reinstall all print related packages and default all print related settings, putting everything that has to do with printing in a state as if the system had just been cleanly installed, but without actually reinstalling Ubuntu? I'm on Ubuntu 20.10 LTS.

---

### Post by brian_p on 2021-10-12
It is relatively easy to do what you request, but the question is - is it really necessary? What are the printer models?

---

### Post by Claus7 on 2021-10-12
Hello,

I would advice you to completely remove the printer(s) from your ubu box. Then, from System Settings->Printers remove all the printers. If you have an hp printer, you have to remove hplip files you installed. It is advised to reboot from time to time for things to take effect. What is beyond me is how you installed non deb files to ubuntu. If by non deb files you mean scripts, then you have to follow the scripts information in order to uninstall them and start anew. Hplip can be installed via scripts. Hplip is also an ubuntu package which you can remove from your system via synaptic package manager. First remove everything and then try to configure anew your printers.

Regards!

---

