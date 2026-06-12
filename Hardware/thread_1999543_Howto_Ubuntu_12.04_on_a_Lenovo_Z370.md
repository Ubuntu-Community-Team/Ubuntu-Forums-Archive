---
title: "Howto: Ubuntu 12.04 on a Lenovo Z370"
date: 2012-06-08
forum: Hardware
---

### Post by cmavr8 on 2012-06-08
[Here's my log/guide]("http://diyistheway.blogspot.gr/2012/06/ubuntu-1210-on-pink-lenovo-z370.html") of bug fixes and optimization tricks for a clean Ubuntu 12.04 install on a Lenovo Ideapad Z370 (Z370a). Battery life is up to 7 hours when idle with Wifi on!

Please feal free to comment here or there, contribute corrections and suggestions.

Thanks



1. fix volume button lockup issue: add the following line to your /lib/udev/rules.d/95-keyboard-force-release.rules file:

```
ENV{DMI_VENDOR}=="LENOVO", ATTR{[dmi/id]product_name}=="IdeaPad Z370", RUN+="keyboard-force-release.sh $devpath common-volume-keys"

```
2. disable nvidia GPU:
```
# add-apt-repository ppa:bumblebee/stable
# apt-get update
# apt-get install --no-install-recommends bumblebee

```
(To check if it works run    $ lspci -vnnn | grep VGA     and "[VGA controller]" should only appear next to the Intel VGA)

3. disable bluetooth on startup by putting:
```
rfkill block bluetooth

```in /etc/rc.local

4. install laptop-mode-tools:
```
# apt-get install laptop-mode-tools

```
5. Set boot options to grub kernel line as seen [here]("http://blog.nexusger.de/?p=104"), put these in /etc/default/grub and run update-grub:
```
quiet splash pcie_aspm=force acpi=noirq i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1

```
6. copy [z370Power]("http://bit.ly/JRBAhy") to /usr/lib/pm-utils/power.d


More things to check/do if needed:
-. VM dirty writebacks: if laptop mode tools doesnt take care of this, uncomment the two lines concerning it in z370Power

-. If powertop whines about audio stuff, uncomment the four lines concerning it in z370Power

---

