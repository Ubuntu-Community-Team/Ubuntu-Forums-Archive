---
title: "Making GPU driver compatible with X.org"
date: 2020-04-25
forum: Hardware
---

### Post by manoaratefy on 2020-04-25
Good morning,

I'm recycling my very old Pentium 4 PC with Xubuntu 18.04. My issue is that its GPU (NVIDIA GeForce 2 MX400) is not fully working with the **nouveau** driver is chosen by default by X.org. When I launch some kind of video with Parole, it freezes.

I think that I should use [the proprietary driver]("https://www.nvidia.fr/Download/driverResults.aspx/49028/fr"), but it only works with X.org 1.12. Is it possible to downgrade X.org to make this driver fully functional? Or is there any other driver I should try to use?

Thanks in advance.

---

### Post by CelticWarrior on 2020-04-25
Welcome.

Bad news. The only driver that works is the open-source nouveau installed by default.
Please understand such hardware is totally obsolete and can't work porperly with any modern OS, Linux or Windows.

---

### Post by CatKiller on 2020-04-25
That GPU is 20 years old, and wasn't very good when it was current. It is not supported by the proprietary driver. Nouveau is the only thing that will make it work.

Even if you were to have a supported GPU and wanted to use the proprietary driver, you wouldn't do so by downloading a file from some website, you'd do it by using the package manager.

The processor is likely 32-bit, too, which is another dead end: support for 32-bit processors has been dropped by recent releases.

I would say that that machine has pressed the end of its useful life. A raspberry pi will give you a machine that is faster, uses *way* less power, and can do things that machine simply isn't capable of, like hardware decoding of modern video formats.

---

### Post by manoaratefy on 2020-04-26
I understand that it is a very old hardware and is not compatible with recent software. This is why I wish to downgrade X.org. Is it possible to downgrade X.org only, or should I go with older Xubuntu?

Note: my goal is to recycle this very old computer to make it a minimum useable. I don't expect very high quality, but hardware replacement is not an option.

---

### Post by CelticWarrior on 2020-04-26
No an neither, again.

The usability you can get from it is with the open-source driver and until the point it too stops supporting the hardware. That's all.

End of discussion.

---

### Post by Yellow Pasque on 2020-04-26
Try a different video player, such as mpv.

> Is it possible to downgrade X.org only, or should I go with older Xubuntu?

No, and any version of Ubuntu supporting the old nvidia 96.xx driver is unsupported/EOL.

---

