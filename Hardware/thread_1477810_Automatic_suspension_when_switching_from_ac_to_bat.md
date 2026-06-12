---
title: "Automatic suspension when switching from ac to battery"
date: 2010-05-09
forum: Hardware
---

### Post by norman86 on 2010-05-09
Hi everyone. I've installed Ubuntu Lucid Lynx Netbook Remix on my Acer Aspire One and I'm having this problem: when I switch from ac power to battery power, the netbook goes to suspension automatically. This is very frustrating, because if I'm working with the wireless connectionm it will be lost after the suspension. Can anyone tell me how to fix this? I've checked the power management options but it didn't help me. Thank you in advance.

---

### Post by P4man on 2010-05-09
Ive seen this before. I think its due to a problem reading the battery level, when you disconnect the AC, ubuntu thinks the battery is critically low and suspends the machine.

Try this: press alt+f2 and type

```
gconf-editor
```
browse to:
/apps/gnome-power-manager/general/use_time_for_policy

set it to false. From the description:
> If time based notifications should be used. If set to false, then the percentage change is used instead, which may fix a broken ACPI BIOS.

So if this helps, you might also want to check if there is a bios update for your machine.

---

### Post by norman86 on 2010-05-09
Thank very much. I have fixed this problem. The option you told me about were checked false already. I have fixed the problem by checking false the option

/apps/gnome-power-manager/actions/event_when_closed_battery

I think the problem happens because when I switch to battery mode the system thinks I'm closind the laptop lid (!). However, thank you for your help.

---

### Post by P4man on 2010-05-09
perhaps you can check this and see if indeed it registers a lid close event, and if so, please file a bug report on launchpad so it can get fixed.

Im not on a laptop right now, so Im not entirely sure where to check, but I think its in /proc/acpi/button/lid/thensomething..status?

---

