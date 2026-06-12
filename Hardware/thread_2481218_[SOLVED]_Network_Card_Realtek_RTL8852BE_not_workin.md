---
title: "[SOLVED] Network Card Realtek RTL8852BE not working Ubuntu 22.04.1 LTS"
date: 2022-11-22
forum: Hardware
---

### Post by brueb44 on 2022-11-22
Hi all,
Ive been trying to fix two persistent issues Ive had with my new laptop since getting it and thought I might try to seek help in these forums here in the hopes someone is kind enough to take some time out of their day to help me with my issues.
Since getting my new laptop Ive had two persistent issues:
1. The network card doesnt seem to work
2. The keyboard doesnt work

For the network card, Ive made a previous [post]("https://ubuntuforums.org/showthread.php?t=2478920") and tried to apply a solution similar to the one given in the comments.
I followed [this]("https://github.com/lwfinger/rtw89") github repo.
After adding the kernel module, I get the following output for the [script]("https://github.com/UbuntuForums/wireless-info") given by the Ubuntu Forums ([pastebin link]("https://paste.ubuntu.com/p/HWbnHfP2n7/")).

Network Card still doesnt work sadly.

If anyone knows any links I could follow or is kind enough to help me out some other way, that would be greatly appreciated !

---

### Post by #&amp;thj^% on 2022-11-22
For the WiFi i would follow the **uninstall given in your link provided, and then follow this:[https://askubuntu.com/questions/1412219/wifi-adapter-not-found-realtek-rtl8852be-wifi-6-802-11ax-pcie-in-ubuntu-22-04](https://askubuntu.com/questions/1412219/wifi-adapter-not-found-realtek-rtl8852be-wifi-6-802-11ax-pcie-in-ubuntu-22-04)

For the Keyboard I'll leave that to someone smarter.

---

### Post by brueb44 on 2022-11-22
Looks like the driver provided by your link works. I can get wireless internet!!

---

### Post by jeremy31 on 2022-11-22
If it doesn't work after a kernel update do ```
sudo apt install dkms
wget https://github.com/jeremyb31/rtl8852be/blob/main/rtw8852be-dkms_1.0.0_all.deb
sudo dpkg -i  rtw8852be-dkms_1.0.0_all.deb
```

---

