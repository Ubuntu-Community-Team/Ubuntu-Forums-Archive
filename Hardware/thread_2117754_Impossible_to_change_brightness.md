---
title: "Impossible to change brightness"
date: 2013-02-19
forum: Hardware
---

### Post by manolomanolo on 2013-02-19
Hi to all.
it happens that I'm unable to change the brightness of my screen.
Impossible at the moment for me to find the original cause.

Sometimes I'm able to change it by Fn+Left/Right arrows to respectively reduce and increase brightness. Some other times I'm not able to do it, but in turn my laptop hangs or snaps. In those cases, most of the times I should only reboot brutally.

Also, I'm not able to change the brightness properly through the power management applet on the task bar. If i just move the slide bar and click on "apply" nothing happens. If I reduce it through Fn+Left arrow key then sliding the bar just set the brightness to the maximum value, even if the bar is not slid to the right end.

Is it a hardware/driver problem? Please find the *lspci | grep Graphics* result below:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Thanks,
regards.

---

### Post by offgridguy on 2013-02-19
Hello, I am wondering which ubuntu version you are using?  I use an acer aspire
5735z, very similar to yours, multi-booted with various linux OS.

They all react differently concerning brightness, but so far all but lubuntu are
adjustable.
edit; thanks to your fn <> tip , i can now adjust lubuntu as well.

---

### Post by manolomanolo on 2013-02-19
Hi,
nice to read that you solved your problem.

I use Kubuntu 12.10, as written on the left side on my user information ;)

However, I remember I've always has such kind of problem also with previous versions of Ubuntu and Kubuntu, also on other laptops...

Any clue?
Thanks.

---

### Post by Toz on 2013-02-19
Have you tried the **acpi_osi=Linux acpi_backlight=vendor** kernel boot parameters?

More info on testing/setting kernel boot parameters [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

More info on backlight debugging/troubleshooting [here]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight").

---

