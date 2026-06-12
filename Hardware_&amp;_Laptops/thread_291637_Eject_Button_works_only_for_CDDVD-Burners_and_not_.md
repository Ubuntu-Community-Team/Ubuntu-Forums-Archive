---
title: "Eject Button works only for CD/DVD-Burners and not for CD/DVD-Drives ?!?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Amnon82 on 2006-11-02
Hi. I'm using Edgy Eft right now. When I push the Eject-Button of my CD-Burner or DVD-Burner with a mounted media inside it opens the tray.

If I try the same with my DVD-Drive it won't. Shure I can use this code:

```
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'
```

... to remove the drive lock, but then Ubuntu seems to have still the media inside.

Is there a way to change it or even edit a file to fake the DVD-drive to a DVD-Burner? I think only on writable drives the eject button works.

I know my drives, so I never want to try writing a disc with it ;)

---

