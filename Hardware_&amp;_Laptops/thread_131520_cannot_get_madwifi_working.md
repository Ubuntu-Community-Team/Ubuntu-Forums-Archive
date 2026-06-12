---
title: "cannot get madwifi working"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by darm on 2006-02-16
Hi once more, everyone.

I've recently got my hands on a Gigabyte pcmci wifi card using ar5212 chipset. So I followed tha faq ([https://wiki.ubuntu.com/WifiDocs/Driver/Madwifi?highlight=%28madwifi%29](https://wiki.ubuntu.com/WifiDocs/Driver/Madwifi?highlight=%28madwifi%29)), but it didn't work out for two reasons:

1. when I install gcc, it gets me to version 4.0, not 3.4; if I try to get 3.4, there's no gcc command at all, bash throws an error

2.(seems less important but anyway). I have 2.6.12-10 kernel - it's the latest one apt-get can give, as far as I understand - and the headers available are for 2.6.12-9

I've already uninstalled madwifi, so I cannot give the error messages I get when trying to modprobe, but well I can reinstall it once more if needed =)

Thanks!

---

### Post by sean_naes on 2006-02-16
madwifi is included in the linux-restricted-modules-(kernel) package, have you tried using that yet?

---

### Post by darm on 2006-02-16
yes, of course, I've plugged the card in and booted up, the restrictrd modules were present, but the card didn't show up in iwconfig. So I followed to FAQs. Do you think I should try reinstalling restricted modules?

---

### Post by darm on 2006-02-20
dammit, my provider decreased the bandwidth tenfold for downloading more than 20 GB this month.And still no answeres on wifi card...pretty sad :(

---

