---
title: "snd_hda_intel Module Incorrectly Blacklisted in Ubuntu 22.04 LTS"
date: 2024-06-23
forum: Hardware
---

### Post by gaesca on 2024-06-23
[FONT=Arial]Hello Ubuntu Community,[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I recently encountered an issue with the `snd_hda_intel` module on my Huawei Mate D15 running Ubuntu 22.04 LTS. The internal speakers would not produce any sound until I manually loaded the `snd_hda_intel` module using `sudo modprobe snd_hda_intel`. After some troubleshooting, I discovered that this module was blacklisted, which prevented it from loading automatically at boot.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]**Steps to Identify the Issue:**[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]1. Sound was not working automatically after a reboot.[/FONT]
[FONT=Arial]2. Manual loading of the module with `sudo modprobe snd_hda_intel` temporarily fixed the issue.[/FONT]
[FONT=Arial]3. Investigating the `/etc/modprobe.d/` directory revealed that the `snd_hda_intel` module was blacklisted.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]**Resolution:**[/FONT]
[FONT=Arial]Removing the module from the blacklist resolved the issue, and sound now functions correctly upon boot.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]**Suggestion for Improvement:**[/FONT]
[FONT=Arial]It may be beneficial for the community to review the default module blacklisting in Ubuntu setups, particularly for configurations similar to mine. This could prevent future users from experiencing similar sound issues.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Thank you for addressing this matter![/FONT]

---

### Post by Yellow Pasque on 2024-06-23
snd-hda-intel is not blacklisted by default (or a lot of people would not have sound). You or a program probably added that line.

> Investigating the `/etc/modprobe.d/` directory revealed that the `snd_hda_intel` module was blacklisted.

What .conf file name?

---

