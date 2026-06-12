---
title: "NI-VISA on Lucid Lynx 10.04"
date: 2010-06-14
forum: Hardware
---

### Post by Nuesel on 2010-06-14
&#65279;Hello,
hope I'm i the correct support category, since VISA are drivers for hardware communication ports.

I tried to install NI-VISA on Ubuntu Lucid Lynx 10.04 (32 bit) using the following instruction:
[http://decibel.ni.com/content/docs/DOC-11652](http://decibel.ni.com/content/docs/DOC-11652)
I tried to install VISA on a fully upgraded Ubuntu as well on “fresh install” from CD without any upgrades. Both the same. I downloaded VISA Runtime 5 Beta and VISA 4.5 from

[http://lumen.ni.com/nicif/US/GB_NIDU/content.xhtml?du=http://joule.ni.com/nidu/cds/view/p/id/1265/lang/en_DE](http://lumen.ni.com/nicif/US/GB_NIDU/content.xhtml?du=http://joule.ni.com/nidu/cds/view/p/id/1265/lang/en_DE)
[http://lumen.ni.com/nicif/D/GB_NIDU/content.xhtml?du=http://joule.ni.com/nidu/cds/view/p/id/2044/lang/de_DE](http://lumen.ni.com/nicif/D/GB_NIDU/content.xhtml?du=http://joule.ni.com/nidu/cds/view/p/id/2044/lang/de_DE)

First of all I had little trouble to alien the rpm files to deb packages. On every conversion I got the same error:
$> alien -k --scripts nipali-2.5.4-b2.i386.rpm
error: incorrect format: unknown tag
nipali_2.5.4-b2_i386.deb generated

$>


Please also look at the more talkative log file alien.odt.
However deb files were generated as alien said. But while installing nipali I got several warnings from insserv “missing LSB tags and overrides”:

$> dpkg -i nipali_2.5.4-b2_i386.deb
(Reading database ... 129311 files and directories currently installed.)
Preparing to replace nipali 2.5.4-b2 (using nipali_2.5.4-b2_i386.deb) ...
Unpacking replacement nipali ...
Setting up nipali (2.5.4-b2) ...
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
insserv: warning: script 'plymouth' missing LSB tags and overrides
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service pulseaudio at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service bluetooth at depth 2
insserv: exiting now without changing boot order!

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
$>

Ignoring these warnings/errors I moved on and I got stuck installing NI-MDNS (item 14 in my instruction manual). The service could not start correctly and therefore I couldn't install the nivisa_5.0.0-b5_i386.deb package.

Where is the problem? Is the alien conversion not successful?
Thanks in advance for any help.

Best regards
Nuesel

---

