---
title: "Asus 1015B AMD Brazos (Fusion) C6 Suspend Resume fix"
date: 2011-04-18
forum: Hardware
---

### Post by SnappyU on 2011-04-18
I have the Asus 1015B, with AMD Brazos (Fusion) C-50 Ontario CPU - AMD 6250 HD GPU.

OOTB, I am running Natty Beta 1 and Beta 2 with no problems mostly.  But if you want GPU acceleration for VLC, you need to install some packages for xvba, libva etc etc.

I also found that when the machine goes into full suspend (C6), it will not resume.  Powering it down and powering up thereafter fails as well.  You need to remove the battery and ac power adapter to power up.

Disabling C6 mode in BIOS allows the system to suspend and resume properly.

Am trying to find patches or workarounds to allow C6, as this will allow longer suspend time.

This may also apply to Acer Aspire One 522 machine with the same AMD Brazos cpu-gpu configuration.

---

### Post by cubeist on 2011-04-19
If you could detail the steps you took to get vlc running with GPU acceleration, that would be great. On my Acer 522 I have tried the libva, xvba from [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/) and built VLC from git, but the CPU still does the majority of decoding and HD 720p+ videos are choppy.

Also, the Acer 522 had no bios options for suspend method, but suspend/resume works with open source ati, but not with fglrx.

---

### Post by SnappyU on 2011-04-25
I believe I got it all working with files from [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)

It will replace vlc as well as a few other files.  When updated, run vlc, enable GPU accel. I got cpu down to 17% ~ 20%.  Disabling gpu accel, cpu shot up to 80+%.

---

### Post by skidmarx101 on 2011-09-06
Disabling C6 in the bios resolved my suspend/hibernate issues, cheers.

I'm still having problems with VLC and GPU acceleration.  I tried the catalysthacks ppa but the update fails to upgrade vlc with the following;

Setting up vlc-nox (1.1.9-1ubuntu2~catalysthacks2) ...
Inconsistency detected by ld.so: dl-tls.c: 79: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx + 1' failed!
dpkg: error processing vlc-nox (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 1.1.9-1ubuntu2~catalysthacks2); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 1.1.9-1ubuntu2~catalysthacks2); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.9-1ubuntu2~catalysthacks2); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 vlc-nox
 vlc-plugin-pulse
 vlc-plugin-notify
 vlc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?  I'm running 11.04 natty on ASUS 1015B.  Thanks

---

