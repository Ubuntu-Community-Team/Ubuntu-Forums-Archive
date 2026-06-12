---
title: "Ubuntu fails to boot (Nvidia hybrid)"
date: 2024-09-22
forum: Hardware
---

### Post by xashyar on 2024-09-22
Hi,

I have a machine with Geforce 960M + Intel 6700 HQ. But I haven't been able to boot Linux on this machine for the last 3 months.

So far I've tried Ubuntu 24.10, 24.04, 22.04, Fedora 40 and Manjaro 24.0.5. All to no avail.

I have already filed a bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/2071680](https://bugs.launchpad.net/ubuntu/+bug/2071680)

 And several other posts on multiple forums:[B]
Ask Ubuntu[/B]: [https://askubuntu.com/questions/1518618/boot-fails-on-nvidia-hybrid-graphics](https://askubuntu.com/questions/1518618/boot-fails-on-nvidia-hybrid-graphics)[B]
Nvidia developer forums[/B]: [https://forums.developer.nvidia.com/t/all-linux-distros-fail-to-boot-on-geforce-960m/307298](https://forums.developer.nvidia.com/t/all-linux-distros-fail-to-boot-on-geforce-960m/307298)
**Manjaro Linux forum**: [https://forum.manjaro.org/t/manjaro-fails-to-boot-nvidia-hybrid/166320](https://forum.manjaro.org/t/manjaro-fails-to-boot-nvidia-hybrid/166320)


Unfortunately the failed boots aren't captured by journalctl, that's why I haven't been able to trace the issue so far.

**Journalctl issue**: [https://askubuntu.com/questions/1520638/unable-to-log-failed-boots-via-journalctl](https://askubuntu.com/questions/1520638/unable-to-log-failed-boots-via-journalctl)

So all-in-all, any help or suggestion leading to at least tracing the issue would be a sign of hope, and I very much would appreciate it.

[B]
More system info[/B]: [https://0x0.st/XV0M.txt](https://0x0.st/XV0M.txt)

---

### Post by Bashing-om on 2024-09-23
xashyar - Hello

When you boot up - Ubuntu - can you boot to Grub's boot menu ?

If so - get to a recovery console as a platform from which to work/explore.
At grub's boot menu > advanced > recovery kernel > root shell.

Then we can carry on.

[INDENT]else we have to do something different
[/INDENT]

---

### Post by xashyar on 2024-09-24
Yess, sure I can. I can also boot into Ubuntu, but only via recovery mode.

---

### Post by Bashing-om on 2024-09-24
xashyar :D

Then my next thought is to know what Nvida driver(s) is installed.
```

dpkg -l | grep -i nvidia

```

where we are looking for the 550 version - only - driver; installed from our software repository.

[INDENT]gots to be a reason
[/INDENT]

---

### Post by xashyar on 2024-09-25
I'm currently running nouveau (note that it doesn't work/boot either), but I have previously tried 560, 550, 535 and 470:

[HTML]rc  libnvidia-compute-470:amd64                             470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA libcompute package
rc  libnvidia-compute-470-server:amd64                      470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA libcompute package
rc  libnvidia-compute-535:amd64                             535.183.01-0ubuntu0.24.04.1              amd64        NVIDIA libcompute package
rc  libnvidia-compute-550:amd64                             550.107.02-0ubuntu1                      amd64        NVIDIA libcompute package
rc  libnvidia-compute-560:amd64                             560.35.03-0ubuntu3                       amd64        NVIDIA libcompute package
rc  libnvidia-gl-470:amd64                                  470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  linux-modules-nvidia-470-6.8.0-38-generic               6.8.0-38.38+1                            amd64        Linux kernel nvidia modules for version 6.8.0-38
rc  linux-modules-nvidia-470-6.8.0-40-generic               6.8.0-40.40                              amd64        Linux kernel nvidia modules for version 6.8.0-40
rc  linux-modules-nvidia-470-6.8.0-41-generic               6.8.0-41.41                              amd64        Linux kernel nvidia modules for version 6.8.0-41
rc  linux-modules-nvidia-470-server-6.8.0-44-generic        6.8.0-44.44+1                            amd64        Linux kernel nvidia modules for version 6.8.0-44
rc  linux-modules-nvidia-470-server-6.8.0-45-generic        6.8.0-45.45+1                            amd64        Linux kernel nvidia modules for version 6.8.0-45
rc  linux-modules-nvidia-535-6.8.0-36-generic               6.8.0-36.36+1                            amd64        Linux kernel nvidia modules for version 6.8.0-36
rc  linux-modules-nvidia-535-6.8.0-38-generic               6.8.0-38.38+1                            amd64        Linux kernel nvidia modules for version 6.8.0-38
rc  linux-modules-nvidia-535-6.8.0-39-generic               6.8.0-39.39                              amd64        Linux kernel nvidia modules for version 6.8.0-39
rc  linux-modules-nvidia-535-6.8.0-40-generic               6.8.0-40.40                              amd64        Linux kernel nvidia modules for version 6.8.0-40
rc  linux-modules-nvidia-535-6.8.0-41-generic               6.8.0-41.41+1                            amd64        Linux kernel nvidia modules for version 6.8.0-41
rc  linux-modules-nvidia-535-6.8.0-44-generic               6.8.0-44.44+1                            amd64        Linux kernel nvidia modules for version 6.8.0-44
rc  linux-modules-nvidia-550-6.11.0-7-generic               6.11.0-7.7+1                             amd64        Linux kernel nvidia modules for version 6.11.0-7
rc  linux-modules-nvidia-550-6.8.0-45-generic               6.8.0-45.45+1                            amd64        Linux kernel nvidia modules for version 6.8.0-45
rc  linux-objects-nvidia-470-6.8.0-38-generic               6.8.0-38.38+1                            amd64        Linux kernel nvidia modules for version 6.8.0-38 (objects)
rc  linux-objects-nvidia-470-6.8.0-40-generic               6.8.0-40.40                              amd64        Linux kernel nvidia modules for version 6.8.0-40 (objects)
rc  linux-objects-nvidia-470-6.8.0-41-generic               6.8.0-41.41+1                            amd64        Linux kernel nvidia modules for version 6.8.0-41 (objects)
rc  linux-objects-nvidia-470-server-6.8.0-44-generic        6.8.0-44.44+1                            amd64        Linux kernel nvidia modules for version 6.8.0-44 (objects)
rc  linux-objects-nvidia-470-server-6.8.0-45-generic        6.8.0-45.45+1                            amd64        Linux kernel nvidia modules for version 6.8.0-45 (objects)
rc  linux-objects-nvidia-535-6.8.0-36-generic               6.8.0-36.36+1                            amd64        Linux kernel nvidia modules for version 6.8.0-36 (objects)
rc  linux-objects-nvidia-535-6.8.0-38-generic               6.8.0-38.38+1                            amd64        Linux kernel nvidia modules for version 6.8.0-38 (objects)
rc  linux-objects-nvidia-535-6.8.0-39-generic               6.8.0-39.39                              amd64        Linux kernel nvidia modules for version 6.8.0-39 (objects)
rc  linux-objects-nvidia-535-6.8.0-40-generic               6.8.0-40.40                              amd64        Linux kernel nvidia modules for version 6.8.0-40 (objects)
rc  linux-objects-nvidia-535-6.8.0-41-generic               6.8.0-41.41+1                            amd64        Linux kernel nvidia modules for version 6.8.0-41 (objects)
rc  linux-objects-nvidia-535-6.8.0-44-generic               6.8.0-44.44+1                            amd64        Linux kernel nvidia modules for version 6.8.0-44 (objects)
ii  linux-objects-nvidia-550-6.11.0-7-generic               6.11.0-7.7+1                             amd64        Linux kernel nvidia modules for version 6.11.0-7 (objects)
rc  linux-objects-nvidia-550-6.8.0-45-generic               6.8.0-45.45+1                            amd64        Linux kernel nvidia modules for version 6.8.0-45 (objects)
ii  linux-signatures-nvidia-6.11.0-7-generic                6.11.0-7.7+1                             amd64        Linux kernel signatures for nvidia modules for version 6.11.0-7-generic
rc  nvidia-compute-utils-470                                470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-470-server                         470.256.02-0ubuntu0.24.04.1              amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-535                                535.183.01-0ubuntu0.24.04.1              amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-550                                550.107.02-0ubuntu1                      amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-560                                560.35.03-0ubuntu3                       amd64        NVIDIA compute utilities
rc  nvidia-dkms-560                                         560.35.03-0ubuntu3                       amd64        NVIDIA DKMS package
rc  nvidia-kernel-common-470                                470.256.02-0ubuntu0.24.04.1              amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-470-server                         470.256.02-0ubuntu0.24.04.1              amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-535                                535.183.01-0ubuntu0.24.04.1              amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-550                                550.107.02-0ubuntu1                      amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-560                                560.35.03-0ubuntu3                       amd64        Shared files used with the kernel module
rc  nvidia-prime                                            0.8.17.2                                 all          Tools to enable NVIDIA's Prime
rc  nvidia-settings                                         510.47.03-0ubuntu4                       amd64        Tool for configuring the NVIDIA graphics driver[/HTML]


There was only 1 time, where 470 worked, but it stopped working after upgrading from **470.239.06-0ubuntu2** to **470.256.02-0ubuntu0.24.04.1**.

Is there any way to switch back to **470.239.06-0ubuntu2** ?

---

### Post by Bashing-om on 2024-09-25
xashyar - Well --

Lots of attempts :(

Let's try this-a-way
Secure boot disabled in Bios - as the driver is 3rd party.
Run in terminal:
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
removes the cruft:
The state is rc, -the package is removed, but the config files are not removed-
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages.
and:
autoinstall to allow the kernel to install the Nvidia version driver it deems fit (I expect the 550 version).

Reboot to see the effect.

[INDENT]is this a Yes !
[/INDENT]

---

### Post by xashyar on 2024-09-26
Bashing-om - unfortunately nothing changed.

'autoinstall'  installs the 560 version (as I'm running 24.10). But I get the same  results (I have tried many clean-installs before as well, but they don't  help either, it's the same even on Fedora, or Manjaro).

This is the screen I get when the booting freezes/fails:


[IMG]https://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAAAAAAD/2wBDAAMCAgICAgMCAgIDAwMDBAYEBAQEBAgGBgUGCQgKCgkICQkKDA8MCgsOCwkJDRENDg8QEBEQCgwSExIQEw8QEBD/2wBDAQMDAwQDBAgEBAgQCwkLEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBD/wAARCABjAUsDASIAAhEBAxEB/8QAHQAAAQQDAQEAAAAAAAAAAAAAAAECAwgEBQYHCf/EAEIQAAEDAwIEAwUGAwUHBQAAAAECAxEABAUGIQcSMUEIE1EJFCJhcRUWMkKBkSOhsSRSYtHhMzRyksHw8RdDVIKi/8QAGQEBAQEBAQEAAAAAAAAAAAAAAAECAwQF/8QAJxEAAgIBBAICAQUBAAAAAAAAAAECEQMSITFRBBMUQfBCYaHB0eH/2gAMAwEAAhEDEQA/AKHaU0lc6iweey1vctNo07i0ZN5C0kl1BfaZKUx0ILwVvtCTXsuJ8GXFfO2r9zhbnTl8q2x6b51lrJEOIc5UKVa/EgDz0ocQspnlKTso7gcf4cLTiHf5HOvcKcxqCz1PZ6afu7JjCDnub7lcZC7flglaShSlEAE/AD2NWk0xwU44ZzCpctfEbqKxjSRUhu8tXWmVNhDbht21hwk2wDqke8ACHG3GyBAnzTzSjsmuf8PSoJ7tHg194UdSW2Qbwljq/TV7fOIxxBbuim2m6VdpV/GUAAlo2TgUop6mI2k89xF8POu F2k7bWup38Icff5BWPtPc78PruSlBX5qAEwWygBQVMwpMgSKtFn HHF5  yOCPGnXTnvlpgTlMnfYooaQld3esBa0AFSG0JaCmoWOcPFUkKiuG4/6Y4jYDwzacVnOJrGptLfeJP2Q2cF5T8LtedDjlwpRUj CUDyyCJITzr5ITFmlKajar SONLY8KsuCecvNS5jSoy2NF7iME3nfxkJfbWyy8ltMweflfTM9OVXUCuny3hJ4yYjLJxCsTibt10PBp20y9u6y4ppSUOIS4FRzJWtKCP70jqK9o0RgONOpdC6X1Va8WrrDO3ulHsbYjJYBtxN0hd0u2bsW3g1KkKSw0fNWVckiIGxkvLLjJpXRWTex3GfUNueXTd4vE3eGUq5uG8vLzjjai0eQJuFLGxAWpMEzyA4llyKlsWot7HgWhPDnr7XPE684TNsW2MzuMZcfvkXSyoWwbQFqStLYUorHMElABWFSkiQRWg0xwzzuqXdSMWb9lav6Wx1zlL1m8dLTimmCA6ltJEqcEzyQDAPSKt5p/w28V9LcRmOKLXELI3L95q57R14pWMS5klsEqYbuXGnm1NPpUGklaVpnbmJJ3ryzhNnOJ rU6vzmQ4o4HArwuNcwN07ncKh83iMhdOTbqIZUUrW8tf8Re6OaJAEVHmbtqqVf9/sh5i5wK1gnihjOErT2NuczlW7R 2dtrnzbdTdwwl9CucDshY5oGxBG9ddp7wccZM/xHu GhxDGPvLUvpRkLrzPs 5LSErIaeSg85KHG1BIHMAoFSRBi1N/wCGbxNXGVt8mnjFpJnJsN4l22ftcELe45bJKvJUlbbUocaHOhYmXAAk8wgDTWPCfjVjeLBzemONSHstk8o7aqXlsQ59lv8APimboRaFHIOZKg0lAQFDy09CIrm88krTQavYqtpzwucatU32UsMVoa6DmIbU9cKuFIYQpsLUjnaW4Ql5JUhYBQTPKYrf3Xgf8Sttciye4XXgdNwzbhPnsGVOgchEL3TuAVDZJPxRXp tNe8X/CNqLJ4m zVlq5riHgfMQMol9Rsw8rzHC0mQhsh9bkIGx5QVIQSAeTuvFj4qV6nY1C HW8jZOJtAgafCR5zyWzyKTy/jdDSFRtzblI3rqnlluqMN0qOMuvB7x3x SscbnNCO4leSdube3cvHW0tl5hpbi0KKSSklLSykkQrlMExXnuveE t Gn2X99dNvYv7cs05CwLhQpLzCoggpJgiUykwoSJG4r0i78V3FpXFK04nZhGHuc1iWX7Fu0u8YDapbUpwqbUyTMpLrgBJ5kzE1xnE/i/qHivfYzK5/FYG0vcWwlgXONx6bdy5CQlKFPmSHVJShCASPwpgzua9EIZNW5htM87NoyP/AGm9hPQUxVqxMeUgH/hFepr45ZReTcyx0LocOOZm1zgbTgWw0l1lry1shEwGHh8TrX4Sr4hymvO8ldIvr 6vm7Vi1TcvLdFvbpKWmgpRUEIBJISJgAk7AV6saae5l0jXmytiNmG v9wU33K22/s7Rn/AOtZXLtv1 dJy7iRXZIwYvuFqels0PnyCkOPsyQPdWuv9wVlhEE9RNIEnmJk/5V1ikyXuYpxdioz7q11/uCk y7Aq3tWh/wDWswJIAEfWgI2iO8100rojbRgnD4/cm1a/5ajOIxokC0a3MTy1sVJOxn9DTFJARzU0RZIt0a44fHQR7m3 1CsLjCI9zbFZ6UydhNCgpMAg oq uPRbZrFYPGE/7qmO3WmnAYsg/wBmH7mtkZJAimwqYiqsUOhbNYvAYyIFvH6mmDAY3aGSJHqdq2rgJITApSgwQB8qeqHQtmnOnsdJ BW/ KmHTlh2QsDseatwU7zSKHxBMbCr6odC2an7t2JE/wAT/mph0zYDYrcEfMVvOX6/rUa5npT0w6CbRpPuvZAfC84N/UGg6UtCf94d/lW5G4MdPWlE9j/Op6MfRdT7NP8Ac 0/ W5 wpPuWyYi Xv/AIOlbwKUfoKlSVfpU9GN/RdcuznjohsxF f WlGg1HpkP/xXRpUZG9SpJgSenqYq jH0NbOYGgXlbjJpj5oNIeH12TtkGiP A11yFgAf1qQKUd5rLwYyapEnBvhxxA4q5pnTXDbHqvsum0VdeUm9atVBpEBRC3VoH5hsDPy61jZ9vU2lM5kNMZtdzaZDFPO2F3bm45i2tCyFtyhRSRzA9CQeu9cjjHVos2FJVHwDespLh7gRXzoxdHdys3P3jzPI6j7XvUpeCQ4kXC4cA6BW 4HaelbK54gazutKs6GuNU5R3T1tcG8bxi7lSrZD8R5gbJgK3P71ywV8 napEkKO561Gk/ols3idSZ5y2trA5rIqtrT/AGDBu3C2z3 BEwnf0ArOd1jqx55Lz pss4tDTbCVLvnVENIUFIQCVfhSoBQT0BAIgirQ C7wucKuOPD3UuqNbOaiXkMTlrOxZbxL0BDTwMuOJDS4Ag/EeVIA3UKzeNHhr4I4HhnxF11wv 92TZ0fqCywtpkVXbT9kvzBFx5o8lCx5bg5CdviWj8Q3Pn90NWl/n5RUm CsbfFHiObhN4nX2pPPTce9h37XuOfz Xl82eeeflAHN1gR0rUnL5R9y5W/kbpxV 55l0pTyiX183NzOSfjPMSZMmTPWrk8OPAJo/VfDLTPEHJ8SM03968Pe3Vrb2mFDnlXjDS3QzPPLoKGl7JAJKYB6x1a/ZjW1nwyympLvX9ycxauLurN1uwPudxZIY81RVJlvmH4XJ5eYcpHxAhHJje6I7RS5XFvicXmrlXETUynWEobaWrL3BUhKBCQDz7ADYDtWztuOvGhlZfa4qauDirr34r 2bgqNxycnmk8/4 X4Z6xtXpWC8JyMt4iNScA/vDfXL Ixl7e2N0zj/Leu3WrMXDKCyon8ZKUnlUZmUkgivdNCey3zGq9LYnNXXEVzFXl/i03V1ZXWEcSbS6VuGCSocwEKCzAUggbGaKWNvSkHfJSHN6s1RqMITn9QZLJpQsuoF5dLeCFlISVDmJgkJSCR1CR6Ctg7xS4kO b52u8857yqyU6V37pLhswBaEydyzA8s9UgbVfvJeyfsnMRZrw/FR9nINDyr8XmLPkuOc4BU0QoFKQkmCeYKIG6QdvDtW DjT2B8WmlvD5bZ7NXeKzdnZ3VzeotALloONrLqgiPhSFNkyoHlB KYmuicEt ERW CrGXy Tz2VvM9nL 4vsjkX13N3dvrK3H3lkqWtaj JRJJJ7msQhHber4PezSaxIevspxFubvHjDX96TZYpQfs7ppnzmW3EqJC0LQFbjlPMIHUGkv8A2amJcydlb4rjzjEMZe8trTGpvsQ627cqdtRcqSIVylYb5lJSNlARIVIra8jH9MaXVlDVp2GxPpQWh0NXLsfBToQeLe48P Z15ftYS1wicwi8DARdPzbB1TaZBQkpJUqVAfCkjrXU4/2YN3nMte4/Dcb9O3Tlki1W40jHvKdaNwkuNpcCVQkFqFJXuFGRt1raywujNMoYtEI ZoQyYMmrgai9n5qXTfGzHcH8nrG1f 2dP5DN43JWdmohxdsgnyXGVHmSSoASCdlAiTIru DPs5MHxX4Yae1g7rjPaezORD3v NyGITDRadLbnlmUqA6Ecw33mK6LNj4smmRQhTJB/DG3SmJZJKiAY/pV  IfszPuRoPUGtW KBu14G0vLn3dWHXLxa/2aU8iiZX0OxgkHcTWZwV9nHo7iFwp05r7UXEvK4O8zlo7d3NorHtFNsULUCJWoEABMkkd 3Wui8nFFck0s fRa5ZiQQKam2JE8u3rVoePXhZ07wvxuisvpvVuVzzOqS8u7aXh1Mu2zTLwaU63BKVJUeblCiCfhMkKke73nsuMPbqYyNpxduHcMHLZp7nwnLdtqeU2EjkDnKSA6knpEGflr5OOk7JodnznNsqQIPSajcY5ZlNfSDBezI0TqqwubjTfHBy5ftbi9slJcwXI37zau U4mfMnlC4BMHrIkV4zxJ8CWX0jx20hwfsNaWd5Z6zD3uGYXaqQGnGeYOtutAkghaQAQSCFA9iK6R8jFLhjS0VGTbK5OYiPSmlkkkdRX0be9lPf2eKZN1xfxbF862olpWMcLQcAHKnnC5jmIBPLsNwD0rzzL zj1cxoC91tgtb4rJPY3DOZW7xvuzjTyHmlrS7bpUSUq5fJehewUW4gAg1peTif2NLKRBglaglMml8hRV0jarZcIvAdrPizwZHGTCarwrFu6u75bG4S4HPKYJSV86QRJUkgJjpBnsOuuvZqa1Y01kMtj ImlchkrFF2Ps1HmtuOv27i21MoWoRJLaoJjcR86fIxXWoaWijK2iXQgJginrZUkyR26VY/gN4KOKnHvSWV17pNONbx9rcKs7RF1chtd4 lTYcQkfkShLgUVq22IG9bC78CHHOwzNzjc7gGcSi3tLy6RcP3CFtvm3tl3BbRyElSlIQQIEAkTG9b92NbORCrwYJKRGx22pqGZUREevyqyes/BFx64faTzGttT6LFrisHbN3N68i8Zc5EuegSolXLsFx HvWHoTwT IDXOlsXrLT2gH7vFZ1hy8sbhNyyPMZQJKiCsFJP5QqCrtWlkhWpND9ivamFJGwmsRzY79qtFxD8D3HDh7ojKa8zem2Rj8Mhp6/SzdIcdt2XGgvzVJH5EzyqgkhQO0Dmqrj8 YodTJrSlGauLJ9kckSDTuYetMnqD6UoMbj1oUkTI37CnpWTuPnUQmSCT0p6VcsHr/nQEwJAgdvnT0LIIPaKi2TSyNqywZKVz1I9RT5Hr 5rHCiBE/61JzeqZP1qA5HGqmxZO88sVlBXUdK1 NcPuLIBiAR/OstKz3mvl20jszISvpJ2qZog/ElVYoUPxEzUja Xf1qELu B3gBobi9oHWOe1LmdWWt3ib2ztUs4G7U3zNOhUqdSltZKRBMnlSBMqFb3jNwF4S6c4X8V87wvy vMnaaMy9hjhcoySHse 8tZTcC5R5SCfJUIKuxUmCobmkGK1JmcKy6nFZa8svPTyOe7vrb50 iuUiR8jT2tUZ1myfxzOXvG7a7IVctJuFhD5HQrTML/AFmuPx5OV2VSSL38I/BrZau4U6L17ecZNU2dtqCyvn8faY/HqUmzv22nXAhs Z8ZWllzZCQpRHKDMx3LfgH1gOFWWyt5xrz4vUNA2AQh/wCz7jHC285SHEFfwIUDAVPIFJgghQI cFtrHUNrbWtpa5y/ZZs3C9bNt3LiEsuHqtABhKvmINbFXErW3uhsU6tzAt1Mm3UyL97yy0erfLzRyn 70rPxp/bI52Wb4eeHJKfFo9wWvuJuXxTlpZOX1pqC2t1WtwP7Il9BKSslI5VEEpWQQJSYNWsvPZ 8RlZBt7AeKTUS7d1Fw/au3CbhTiVrAIPMh4BQWNlqEHpsqvlLZahybF2m/avrhu5SIS6h1SVgRGygZG230rqbPjDxHx7TLNnrzUDCLbmLKW8o kNlQglIC9pGxjtW1gle72EpJ8H0buPAZx2XdWePsfEnmXMddst29ytxF6nykcillEebCmwpECSN1JJArVab8B qtZ5u24o4zxRXeafssg/afarFtde tN2ylNrShanOdLqVpWgo6DqCZg0A/wDXDio2Ia4ialTDXkCMtcbNzPJ P8M7x0msfD8Y JGBtl2mF1xnrFly599cRbZJ5sLuBv5pCVbr/wAXWr6Zdk1JFy9GcNOJOa8VfEjhJYcbuIDA0xZXz9vmGbx5x5a0NpLIuIVywfMKTsJ3AgkV31z4KdaYnma1j4hdS3GPwT2Kcw99Yt3BatHFXfu7oLa1ny1tFyUFChCVE7CRXzzxPFziHhtRXWsMXrXN2ucvQpNxkWb91Fy6FRzBbgVzKmB1J6CthbceeLrFrfWTfEnU3kZJC27xs5Z9SLhC/wASVpKoIPf1qvBJu0y610X9T4GdX5jizZ5fOeKO5vM9cKu3lXHu9ynLqsbZ33damlqXuQVcih FPMI5kmtL4efDzxK1bxZ4p4XGcftS4O30XenSjl1auuKu71pCVptgv4oS2hKB8P1CSmqONcc K7ebtNTHiLqNWXx6VItL1WTeU wFABQQsqkAgAEd4E9KdpvjbxO0xmMnqPA69z1hlcyFfaN4xfuIeu YyfNUDK5O8nea36Ztck1pH0ey3gr41J1LhNQXfihyb2qsdfe6Y  dZuHFW1s62tZLZLhUlRKF8yCeUgHedj5xpHG JPUfiG1H4dNWcdtVWrmDtbrKLyGPfW60t9DaHWHFHYoQsqQSCRBkDfrUV3xO8cX737Rd4raoVcBtlrzDlHZ5Wlc7Q6/lVuPQk prXYvj7xZxut7riTZcQM2zqe8QW38qm8V7w6ggApUr8whKdjtsPSqsE2mtiakfS5fhy8UNt7pdu Lq8XkLC6s0WPMl/wAmFqLawsEnmUCopCVAhYMKKdo5djH IXiHxw1R4euLHiBu8fjbXTCsw5fYu1Ybt7y0XypHmIUlPIkpcXzgn8p3iFVQlPiX43i6dvFcUtTF18OJdWci4StK1IUoHfupts7d0A1rctx34o5/VN9rbLa5y1xnMhZqxtzequCHXrRSPLWyojYoKDBTEGa1HxZ1ToqyLo r2B4NcXOH2iMjiNKeJfIXFvp7BpRa2uTwTDtgB5JcAS6sElrlSACkqKB1kACq86Z154gdceHDUPiKx/iHy32tpB5xq5wnkNpbFs2ps8xWB8S1DlUJSQQkgmSaqI14rePNlp3H6YsuKeoWMdiUJasrdF4QlpCfwpHcgDYAzA26bVytlxm4hYTQeU4bYnVl/a6bzjqX8hjW3IZfWmIKh iZA2PKmZgVqHiu1qojnZ6EfGBx Yyd5krfiNkbR  vV37wtw22gvrU0pawgJgcymGiQBEpPqqewxXtFfEjaqu3b7VNlknXmUMsu3mMYWu2KQQFtEJHKozJO8kAmqprulLVzLPX5U1D8DY/ a9noxt7oxbLXYv2iPiWwmMtcZba3afRZp5GnLrHsPORy8oBWUyQBB37gE1it 0E8RdvZYrHjWDC2sZCf4mPZWq6SAoFL5Kf4qSFqBB6z671VxVxtsSN/Wml9RPXrvV Pi6FsuU97SrjkwG2NPWelsHYoUlarGyw6EsrI/FIJJhX5gD2HTetdee0c4/fdy6wrV7hEOXbF0ybxOMbFwgvrUpS0qGwUkrVy7d95O9VHL6iY/nUa3SVAEmaq8fEndGbnZZngP40 KnAPRy9H6RXi3ccu VkOW9sw6tClcvmISqQQlfImR8pEV1LHtFuMrmZt8tlrLT R9zRlEssXNhzNpN8oFZgK/Ikcqf8KlAzJqoKnzywP zR7wYmTMzVfj4pcxNW1wW34l 0H4p8Q Huf4dZDDactrPU7LLF45aWRacCUkF1YPNBW6QOYkGPyxXQ8PvaP694Z6G03ofTukdPKtNO4gY1Tlyha13ahzcjiiFDlCeY/CNiSZ6wKSF8lwATIEUqrlXLAMmafHxJVQtlotd PnihqvQ2Q0NcYrAotsvh1Ye fbt1h24SWEM ar448wNtgDaB6VVJ1ZccK42O9K66VGY2HzqAkhXN9a1GMYbRVAkJ9T 9ICRE/SmAEQP lLO8HtuK0CQKIinBRPX9ajB7k04SDWATc/pJjpSpUog/CD2qEGd47 tOhQE9qAmCiEzP1qQOJHqP1rGSoiR2p8g71GwcjjVJ9zbH1/rWWFbxM9q1 NXFonfoTWWlW29fOStHZ8kyV1KhQJ VY8ie/wC9PSruD 1VKiGX5mwT nWl55VAPSscLHX1 dKkhRqmTLS6dhPenF3uT02rFCtxJ/Wl595/nQhmIc5Tt3qZL45e2/Q1ghRAHSnpWB/oaAy1XBCZM lHnBQiY/zrEKj3j1maAuNp71UTczUOgnePU04PCPrWFz77bfrS ZIgq6VojM3zhvA6mned0jpWGHPp60pdESP61uLBmB7YyR6U8PQPhNYPmAdDPanc/aYiusaBmC4J6HtR7xywO3rWHzbTvvS8xA6mtAyVPqXtO0AUxx0kiTUPOCob703n33/r1oTgkU4TuD8qXnIAg7DeoSokdqXmHqf1rSKSlXMSdhSBQBnf02qOfXoO9AJ6dvWtpglDh33O370gVKgSDTJ3ImgKjcD/AMVQSLcM7HpvSSBtNRgyAQPlRJEj50A dz13oJ7bD9aYmIkT84oKgAd6Aao77mmST360CT36770ft/rQDuqdj0/rR0kkb/KkH6RRIkEn/SowPBAPWnCYIIAmo9wCR0p0k7k1kD9unehJEETBNIIG07USImgHhRiR tHmRsJ/emE7fPsKQqAPWP0qNWDk8Yf7OEz0J7VlAwmZmO1YWN2YifzHpWWkV8 K2OrZMkyAZM tOBIqFJ6SCakBk1qjNkkwOYUoO2xNRySKdzb9B8qUQmSrl/ESacDPTr6VCDH/AJp6CRuR0HrVoWTA/vSyYjoIpgUPnRMbTSiWiUq5k83cbUcxkU1EkFPY7UgkmZqktkoUJkA0FXX0qP6bUTJ3JMUBNzweVJkkUFSv8qiBP4d470oVB/WuiQJeaIBH7VIZPWsdJMnr06VID8jB7iuyVE4JOaYmduho5yZk7GmA78oA/elJ9QTQbjyd aZApvXqCaAduu1E s04AsnrtFPG4Anr1pk7iAaVJ9ZJ6VpFHGCIA2O1EAJ Ront60mx/StoClUDYbj0oRJG56UhA lABHTpVAomfxbdaD2Jnr1pEwJidqCmfhk/WaAU7UxXWTT94EjrTTHcCR2oBo m80fqaUSIUE0BJPSIoAExsKCCB22G1A3/AFG1OgQB0qAEye3UTThMAT 1AgfPbaKCCAfpWQAAG070fTYUvWCBSdASJEnfes7gSe5/ak DvNIqYnpt0mjl9QTWgcljSPKUCPzVmpO8TsawMZJQsT3rO2/yrwR4NvkekCBP6CnAkGJ7UwJn4h 1PHSSI9K0QdIo9DSBO1Lv6UI2OBjaKkSohMg94iowQBUh/wBmkExuaBjiSO/zp36dKZ hpxAgACd lVRZBwMEH VKrYmI36Unfr2omYn07VVECxvI3peYR23pN95jakAkSRXRRA4nsDSgjbb60gBAilgjqd62o0TgVMT0p6DuZnbtUY/1indJiYqlJJkSN4pZIIPWkSfWiYPSflQDpSAIpQZOxpCRMTsaWd4n0rSAoJB/6CnkwJFMBjbqKWIBMVpKwAKuUgHvTjv2269aBCOvWgEzEdutaASO1OVI3H7Um0QD 9GwVuQKAB8jQY5iYoPLEjqKN 386AQCAI6U1QHYRFPkHrQYAkAkCqBhGw2joN6AOsbRToEzuaUCTt2qAAE83enCO0xRsOsEilA227VaAm8b/wBKX6TBoA9N6dEdBt8qjQGRABmkIn lOiTsOkUsEnck7du4qUCKATCgNqFpBUdzTz13FNj/AA/zpQOPxf4V/Ws7okAd6KK dDg6S5Hg/ER6Up2gUUV0Rljh0pR3 VFFAhRsJqWAW0T86KKq4MsASOlO/LzdwaKK6xA6dqWBJFFFaA6ACUgbUiaKKAVQA3A3M0ev0oooc5ci9Ekj60vRIj1oooX9I4AEgEU5X4oooobFHf6xR8/nRRWwPHQmnoAKST60UVUBJMH6U6P5UUVoCEkJJntS9p7xRRQAOhNAooogIrZO3eg7jm70UUYDoBHenjr 1FFaAqRPX5047CaKKIBJ9e1B2Ej/AL2oooBQPijtSgD tFFT6IuBiv60gSI7/vRRUKf/2Q==[/IMG]

---

### Post by xashyar on 2024-09-26
Bashing-om - unfortunately nothing changed.

'autoinstall'  installs the 560 version (as I'm running 24.10). But I get the same  results (I have tried many clean-installs before and it's the same even on Fedora, or Manjaro).

This is the screen I get when the booting freezes/fails:


[IMG]https://ibb.co/dWwMpLw[/IMG]
[IMG]https://ibb.co/dWwMpLw[/IMG]
[https://ibb.co/hHW9SMN](https://ibb.co/hHW9SMN)

---

### Post by Bashing-om on 2024-09-26
xashyar; Yuk -

I am really floundering here too - as I have no idea what "EFI stub" is telling us.

However -- might give us a hint of what the kernel thinks:
```

less /var/log/gpu-manager.log

```

[INDENT]a know-it-all --- I am not
[/INDENT]

---

### Post by xashyar on 2024-09-27
Bashing-om; Thank you for your patience! 

I have prime-select currently set to **on-demand**, and it's worth noting that if I switch it into **nvidia**, I get a black-screen even if I boot via recovery mode from the grub menu.

Here's the log output, and nvidia is shown to be blacklisted:

[HTML]log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/6.11.0-8-generic/kernel
Looking for nvidia modules in /lib/modules/6.11.0-8-generic/kernel/nvidia-560
Found nvidia.ko module in /lib/modules/6.11.0-8-generic/kernel/nvidia-560/nvidia.ko
Looking for amdgpu modules in /lib/modules/6.11.0-8-generic/kernel
Looking for amdgpu modules in /lib/modules/6.11.0-8-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? yes
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:191b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver.
Vendor/Device Id: 10de:139b
BusID "PCI:1@0:0:0"
can't open /sys/bus/pci/devices/0000:01:00.0/boot_vga
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
can't open /sys/bus/pci/devices/0000:01:00.0/boot_vga
Chassis type: "10"
Laptop detected
can't access /etc/u-d-c-nvidia-runtimepm-override file
can't open /sys/module/nvidia/version
Warning: cannot check the NVIDIA driver major version
Support for runtimepm not detected.
You can override this check at your own risk by creating the /etc/u-d-c-nvidia-runtimepm-override file.
Is nvidia runtime pm supported for "0x139b"? no
Checking power status in /proc/driver/nvidia/gpus/0000:01:00.0/power
Error while opening /proc/driver/nvidia/gpus/0000:01:00.0/power
Is nvidia runtime pm enabled for "0x139b"? no
Skipping "/dev/dri/card0", driven by "simpledrm"
Skipping "/dev/dri/card0", driven by "simpledrm"
Skipping "/dev/dri/card0", driven by "simpledrm"
Skipping "/dev/dri/card0", driven by "simpledrm"
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
NVIDIA hybrid system
can't open /sys/module/nvidia/version
Creating /usr/share/X11/xorg.conf.d/11-nvidia-offload.conf
Setting power control to "auto" in /sys/bus/pci/devices/0000:01:00.0/power/control
Loading nvidia with "no" parameters[/HTML]

---

### Post by Bashing-om on 2024-09-27
xashyar - at least we have some Hints :D

> 
can't access /run/u-d-c-nvidia-was-loaded file

Is nvidia loaded? no

Is nvidia blacklisted? yes

Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver.

can't open /sys/module/nvidia/version

Hummm ...
It's possible that when you last switched from Intel to nvidia that the process wasn't completed. So you have nvidia loaded & blacklisted. You could try either - or both:
switch to intel, reboot, switch to nvidia, reboot, i.e
```

sudo prime-select intel
reboot
sudo prime-select nvidia
reboot

```

Now is Nvidia still blacklisted ?
```

ls /etc/modprobe.d/
ls /lib/modprobe.d

```

If still blacklisted:
```

sudo rm /lib/modprobe.d/blacklist-nvidia.conf

```
may be worth a shot.

[INDENT]be nice if it were this simple --- hope !
[/INDENT]

---

### Post by cryofreeze666 on 2024-09-28
question, i'm a new guy so don't expect much.  are you running multiple drives or are you partitioning if you are running multiple o.s.'s?  the reason i ask is this, when i first started trying to install multiple o.s.'s my ubuntu o.s. was continually being installed on the second drive when i was leaving more than half the primary drive for it to install in, before i put all my windows programs in the trash.  i solved that by unplugging second ssd when installing second o.s.

the next reason i ask that question is, i just found out why i wasn't able to get my o.s. to boot period.  my problem started and i got the grub screen too, but i wasn't able to get to it right away so i turned of computer with switch.  when i got enough time to work on it again, it didnt go back to the grub screen it would freeze on /dev/nvme0n1p2: (blah blah blah) screen.  my problem was i overlooked the simplest thing, i forgot to check whether my primary drive was dead or not.

have you tried something simple to help you troubleshoot like full installing ubuntu on a larger flash drive flash drive (like 256gb) and seeing if it will boot from there?  it could help with your troubleshooting.

---

### Post by xashyar on 2024-10-03
Hi Bashing-om, 

When I switch to nvidia, something strange happens:

Ubuntu boots (only via 'recovery mode' of course), but it doesn't reach the login screen (I get a blank screen instead of the login screen).

However, that doesn't generate a blacklist-nvidia.conf by itself. Let me recount the steps:


```

1. sudo prime-select intel
2. reboot
3. sudo prime-select nvidia
4. reboot
// ubuntu fails to reach the 'login-screen', therefore switching back to intel (no 'blacklist-nvidia.conf' generated yet)
5. sudo prime-select intel
// ubuntu once again fails to reach the 'login-screen'
6. reboot
// ubuntu reaches the 'login-screen' and now 'blacklist-nvidia.conf' is generated.

```

I guess removing /lib/modprobe.d/blacklist-nvidia.conf, prevents you from reaching the login screen, even when you have switched prime-select to intel.

---

### Post by Bashing-om on 2024-10-03
xashyar - Hummm ...

Well at lest we have another data point --

As we have the error:
> 
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.


does the symbolic link exist ?
show:
```

ls -al /sys/bus/pci/devices/0000:01:00.0/driver

```

well past my end_of_session time here -- will check back in tomorrow by that time I will have a fresher mind and not as liable to silly mistakes.

[INDENT]gots to be a reason
[/INDENT]

---

### Post by xashyar on 2024-10-03
Hi, looks like it doesn't exist:
[HTML] ls: cannot access '/sys/bus/pci/devices/0000:01:00.0/driver': No such file or directory[/HTML]


The '/sys/bus/pci/devices/0000:01:00.0/' directory exists, but there's no 'driver' inside.

---

### Post by Bashing-om on 2024-10-03
xashyar; Ouch !

I am now aware that there exist "issues" with the 550/560 drivers in 24.10:
[https://ubuntu-archive-team.ubuntu.com/component-mismatches.html](https://ubuntu-archive-team.ubuntu.com/component-mismatches.html)
As to weather this affects you - I do not have the knowledge to say.

How about trying an older version driver ?
what shows:
```

sudo ubuntu-drivers list

```

[INDENT]it's broke, Sam[/INDENT]

---

### Post by xashyar on 2024-10-04
Bashing-om; Yup...

Should I try one of the older ones and see if, '_ls -al /sys/bus/pci/devices/0000:01:00.0/driver'_ returns anything?
> nvidia-driver-550, (kernel modules provided by nvidia-dkms-550)
nvidia-driver-535, (kernel modules provided by nvidia-dkms-535)
nvidia-driver-560, (kernel modules provided by linux-modules-nvidia-560-generic-hwe-24.04)
nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic-hwe-24.04)
The pity of it is, that I was on 24.04 before upgrading to 24.10, so I've tried 535 and 470 as well, both to no avail, and as I mentioned before the *only* version that I remember working was **470.239.06-0ubuntu2 **and it stopped working as well, after upgrading to **470.256.02-0ubuntu0.24.04.1**.
[INDENT]Besto!
[/INDENT]

---

### Post by Bashing-om on 2024-10-04
xashyar; Yukkie poo - on me too.

I have seen this:
> 
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
can't open /sys/bus/pci/devices/0000:01:

before, and have not been able to find the fault :( I was hopeful in your case that here was put a dropped sym link - not !)

I am at a dead end and do not have the skills to push forward. If no other offers assistance - might be best at ^that time to bite the bullet and do a fresh clean install and see then what results.

[INDENT]drop back 5 yards, and punt[/INDENT]

---

### Post by xashyar on 2024-10-05
Okey thanks.

But just to conclude so far, are we clear that this is definitely an **Nvidia** issue? (In that case I wonder why Nouveau never works)

When I run Ubuntu live from a thumb drive, the Nouveau driver works fine, it's after installing that things go wrong.

Therefore could this be related to UEFI firmware, Linux Kernel or anything else?

Also did the _ubuntu-drivers list_ result return anything useful?

As for fresh install I've bit the bullet so many times, not sure if anything's different this time.

[INDENT]Best,
[/INDENT]

---

### Post by Bashing-om on 2024-10-05
xashyar -- Welp -
So long as you are willing to continue to struggle with this to find a solution - I too am willing to hold your hand :D

As to exclusively an Nvidia issue - I am not prepared to make that claim. You have tried different distros and all the available Nvida drivers - seems to me this is a more a OEM implementation of their hardware interface - but yet I do not know.
What we can do to gain another data points
1) See what results booting up with the "nomodeset" boot parameter 
(from here - with the prior prudent planning - might have better results to install an Nvidia driver)
2) Reproducible with either/both X11/Wayland environments ?
see here what we are working from:
```

systemctl status display-manager
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
echo $XDG_SESSION_TYPE

```

[INDENT]I am all in for fighting, as I too step up on the learning curve
[/INDENT]

---

### Post by xashyar on 2024-10-06
Bashing-om -- Thank you;
That is now very heartwarming to hear :P

1) I've put "nomodeset in place, and the _/etc/default/grub_ is now looking like this:
[HTML]GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""[/HTML]

2) As for X11/Wayland, it's currently on wayland but I get the same result with X11 regarding the boot:

systemctl status display-manager
[HTML]&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/usr/lib/systemd/system/gdm.service; static)
     Active: active (running) since Mon 2024-10-07 06:17:31 +0330; 10min ago
 Invocation: d25bcf7cb0974581aa404d93c770e9ad
    Process: 1705 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
   Main PID: 1720 (gdm3)
      Tasks: 4 (limit: 18305)
     Memory: 6.9M (peak: 57.1M)
        CPU: 945ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;1720 /usr/sbin/gdm3

Oct 07 06:17:31 xashyar-N552VW systemd[1]: Starting gdm.service - GNOME Display Manager...
Oct 07 06:17:31 xashyar-N552VW systemd[1]: Started gdm.service - GNOME Display Manager.
Oct 07 06:17:31 xashyar-N552VW gdm-launch-environment][1729]: pam_unix(gdm-launch-environment:session): session opened for user gdm(uid=120) by (uid=0)
Oct 07 06:17:31 xashyar-N552VW gdm-launch-environment][1729]: pam_systemd(gdm-launch-environment:session): New sd-bus connection (system-bus-pam-systemd-1729) opened.
Oct 07 06:17:58 xashyar-N552VW gdm-password][2524]: gkr-pam: unable to locate daemon control file
Oct 07 06:17:58 xashyar-N552VW gdm-password][2524]: gkr-pam: stashed password to try later in open session
Oct 07 06:17:58 xashyar-N552VW gdm-password][2524]: pam_unix(gdm-password:session): session opened for user xashyar(uid=1000) by xashyar(uid=0)
Oct 07 06:17:58 xashyar-N552VW gdm-password][2524]: pam_systemd(gdm-password:session): New sd-bus connection (system-bus-pam-systemd-2524) opened.
Oct 07 06:17:58 xashyar-N552VW gdm-password][2524]: gkr-pam: unlocked login keyring
Oct 07 06:18:06 xashyar-N552VW gdm3[1720]: Gdm: Child process -1774 was already dead.
[/HTML]
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
[HTML]ubuntu   ubuntu:GNOME
[/HTML]
echo $XDG_SESSION_TYPE
[HTML]wayland[/HTML]

---

### Post by Bashing-om on 2024-10-06
xashyar - Hey !

This may be real relevant:
> 
Gdm: Child process -1774 was already dead.


Off the top of my head I do not know what this implies to the drivers - but; can not be good.

excuse me while I do the homework to know more.

-inquiring minds want to know-

---

### Post by Bashing-om on 2024-10-08
xashyar - Regrets :(

Beyond my skills presently to understand this; I am making no forward progress to proffer a viable fault-finding procedure - that I feel might be productive. I am stumped.

Hopefully another here will step forward with suggestions.

-A know-it-all - I am not-

---

### Post by xashyar on 2024-10-09
Bashing-om; Thanks for the look out!

I just wanted to add another data point which might be of importance.

I ran_ systemctl status display-manager_ again this time with **X.org/X11** as session manager, and got pretty much the same result:
[HTML]&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/usr/lib/systemd/system/gdm.service; static)
     Active: active (running) since Wed 2024-10-09 09:56:55 +0330; 2min 28s ago
 Invocation: 0e13b185343e450baacca55df7080969
    Process: 1753 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
   Main PID: 1778 (gdm3)
      Tasks: 4 (limit: 18305)
     Memory: 6.8M (peak: 56.9M)
        CPU: 551ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;1778 /usr/sbin/gdm3

Oct 09 09:56:55 xashyar-N552VW systemd[1]: Starting gdm.service - GNOME Display Manager...
Oct 09 09:56:55 xashyar-N552VW systemd[1]: Started gdm.service - GNOME Display Manager.
Oct 09 09:56:55 xashyar-N552VW gdm-launch-environment][1788]: pam_unix(gdm-launch-environment:session): session opened for user gdm(uid=120) by (uid=0)
Oct 09 09:56:55 xashyar-N552VW gdm-launch-environment][1788]: pam_systemd(gdm-launch-environment:session): New sd-bus connection (system-bus-pam-systemd-1788) opened.
Oct 09 09:57:06 xashyar-N552VW gdm-password][2586]: gkr-pam: unable to locate daemon control file
Oct 09 09:57:06 xashyar-N552VW gdm-password][2586]: gkr-pam: stashed password to try later in open session
Oct 09 09:57:06 xashyar-N552VW gdm-password][2586]: pam_unix(gdm-password:session): session opened for user xashyar(uid=1000) by xashyar(uid=0)
Oct 09 09:57:06 xashyar-N552VW gdm-password][2586]: pam_systemd(gdm-password:session): New sd-bus connection (system-bus-pam-systemd-2586) opened.
Oct 09 09:57:07 xashyar-N552VW gdm-password][2586]: gkr-pam: unlocked login keyring
Oct 09 09:57:21 xashyar-N552VW gdm3[1778]: Gdm: Child process -1851 was already dead.[/HTML]

---

### Post by Bashing-om on 2024-10-09
xashyar -

Well with X11 as your DE Xorg's log file might give us some additional info.
```

cat .local/share/xorg/Xorg.0.log

```

[INDENT]is a thought
[/INDENT]

---

### Post by xashyar on 2024-10-09
Sure thing:
[HTML][  1308.803] (--) Log file renamed from "/home/xashyar/.local/share/xorg/Xorg.pid-8392.log" to "/home/xashyar/.local/share/xorg/Xorg.0.log"
[  1308.804] 
X.Org X Server 1.21.1.13
X Protocol Version 11, Revision 0
[  1308.804] Current Operating System: Linux xashyar-N552VW 6.11.0-8-generic #8-Ubuntu SMP PREEMPT_DYNAMIC Mon Sep 16 13:41:20 UTC 2024 x86_64
[  1308.804] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.11.0-8-generic root=UUID=0512cb18-c262-4d4d-b85e-042d2bc678f7 ro recovery nomodeset dis_ucode_ldr
[  1308.804] xorg-server 2:21.1.13-2ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[  1308.804] Current version of pixman: 0.42.2
[  1308.804]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1308.804] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1308.805] (==) Log file: "/home/xashyar/.local/share/xorg/Xorg.0.log", Time: Wed Oct  9 22:57:00 2024
[  1308.805] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1308.806] (==) No Layout section.  Using the first Screen section.
[  1308.806] (==) No screen section available. Using defaults.
[  1308.806] (**) |-->Screen "Default Screen Section" (0)
[  1308.806] (**) |   |-->Monitor "<default monitor>"
[  1308.807] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1308.807] (**) Allowing byte-swapped clients
[  1308.807] (==) Automatically adding devices
[  1308.807] (==) Automatically enabling devices
[  1308.807] (==) Automatically adding GPU devices
[  1308.807] (==) Automatically binding GPU devices
[  1308.807] (==) Max clients allowed: 256, resource mask: 0x1fffff
[  1308.808] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1308.808]     Entry deleted from font path.
[  1308.808] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1308.808]     Entry deleted from font path.
[  1308.808] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1308.808]     Entry deleted from font path.
[  1308.808] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1308.808]     Entry deleted from font path.
[  1308.808] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1308.808]     Entry deleted from font path.
[  1308.808] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1308.808] (==) ModulePath set to "/usr/lib/xorg/modules"
[  1308.808] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1308.808] (II) Loader magic: 0x630f0d54b020
[  1308.808] (II) Module ABI versions:
[  1308.808]     X.Org ANSI C Emulation: 0.4
[  1308.808]     X.Org Video Driver: 25.2
[  1308.808]     X.Org XInput driver : 24.4
[  1308.808]     X.Org Server Extension : 10.0
[  1308.809] (++) using VT number 2

[  1308.813] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_37
[  1308.814] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1308.814] (II) Platform probe for /sys/devices/pci0000:00/0000:00:02.0/simple-framebuffer.0/drm/card0
[  1308.815] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 14 paused 0
[  1310.137] (--) PCI:*(0@0:2:0) 8086:191b:1043:1d8d rev 6, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[  1310.137] (--) PCI: (1@0:0:0) 10de:139b:1043:1d8d rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  1310.137] (II) LoadModule: "glx"
[  1310.141] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1310.144] (II) Module glx: vendor="X.Org Foundation"
[  1310.144]     compiled for 1.21.1.13, module version = 1.0.0
[  1310.144]     ABI class: X.Org Server Extension, version 10.0
[  1310.144] (==) Matched modesetting as autoconfigured driver 0
[  1310.144] (==) Matched fbdev as autoconfigured driver 1
[  1310.144] (==) Matched vesa as autoconfigured driver 2
[  1310.144] (==) Assigned the driver to the xf86ConfigLayout
[  1310.144] (II) LoadModule: "modesetting"
[  1310.145] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1310.146] (II) Module modesetting: vendor="X.Org Foundation"
[  1310.146]     compiled for 1.21.1.13, module version = 1.21.1
[  1310.146]     Module class: X.Org Video Driver
[  1310.146]     ABI class: X.Org Video Driver, version 25.2
[  1310.146] (II) LoadModule: "fbdev"
[  1310.146] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1310.147] (II) Module fbdev: vendor="X.Org Foundation"
[  1310.147]     compiled for 1.21.1.11, module version = 0.5.0
[  1310.147]     Module class: X.Org Video Driver
[  1310.147]     ABI class: X.Org Video Driver, version 25.2
[  1310.147] (II) LoadModule: "vesa"
[  1310.147] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1310.148] (II) Module vesa: vendor="X.Org Foundation"
[  1310.148]     compiled for 1.21.1.11, module version = 2.6.0
[  1310.148]     Module class: X.Org Video Driver
[  1310.148]     ABI class: X.Org Video Driver, version 25.2
[  1310.148] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1310.148] (II) FBDEV: driver for framebuffer: fbdev
[  1310.148] (II) VESA: driver for VESA chipsets: vesa
[  1310.148] xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)
[  1310.148] (II) modeset(0): using drv /dev/dri/card0
[  1310.148] (WW) Falling back to old probe method for fbdev
[  1310.148] (II) Loading sub module "fbdevhw"
[  1310.148] (II) LoadModule: "fbdevhw"
[  1310.148] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1310.149] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1310.149]     compiled for 1.21.1.13, module version = 0.0.2
[  1310.149]     ABI class: X.Org Video Driver, version 25.2
[  1310.149] (EE) open /dev/fb0: Permission denied
[  1310.149] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[  1310.149] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1310.149] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[  1310.149] (==) modeset(0): RGB weight 888
[  1310.149] (==) modeset(0): Default visual is TrueColor
[  1310.149] (II) Loading sub module "glamoregl"
[  1310.149] (II) LoadModule: "glamoregl"
[  1310.149] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  1310.171] (II) Module glamoregl: vendor="X.Org Foundation"
[  1310.171]     compiled for 1.21.1.13, module version = 1.0.1
[  1310.171]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1310.224] (II) modeset(0): Refusing to try glamor on llvmpipe
[  1310.226] (II) modeset(0): glamor initialization failed
[  1310.226] (II) modeset(0): ShadowFB: preferred NO, enabled NO
[  1310.226] (II) modeset(0): Output None-1 has no monitor section
[  1310.226] (II) modeset(0): EDID for output None-1
[  1310.226] (II) modeset(0): Printing probed modes for output None-1
[  1310.226] (II) modeset(0): Modeline "1920x1080"x60.0  124.42  1920 1920 1920 1920  1080 1080 1080 1080 (64.8 kHz eP)
[  1310.226] (II) modeset(0): Output None-1 connected
[  1310.226] (II) modeset(0): Using exact sizes for initial modes
[  1310.226] (II) modeset(0): Output None-1 using initial mode 1920x1080 +0+0
[  1310.226] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[  1310.226] (==) modeset(0): DPI set to (96, 96)
[  1310.226] (II) Loading sub module "fb"
[  1310.226] (II) LoadModule: "fb"
[  1310.226] (II) Module "fb" already built-in
[  1310.226] (II) UnloadModule: "fbdev"
[  1310.226] (II) Unloading fbdev
[  1310.226] (II) UnloadSubModule: "fbdevhw"
[  1310.226] (II) Unloading fbdevhw
[  1310.227] (II) UnloadModule: "vesa"
[  1310.227] (II) Unloading vesa
[  1310.229] (==) modeset(0): Backing store enabled
[  1310.229] (==) modeset(0): Silken mouse enabled
[  1310.230] (II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
[  1310.230] (==) modeset(0): DPMS enabled
[  1310.231] (II) Initializing extension Generic Event Extension
[  1310.231] (II) Initializing extension SHAPE
[  1310.231] (II) Initializing extension MIT-SHM
[  1310.231] (II) Initializing extension XInputExtension
[  1310.232] (II) Initializing extension XTEST
[  1310.232] (II) Initializing extension BIG-REQUESTS
[  1310.232] (II) Initializing extension SYNC
[  1310.232] (II) Initializing extension XKEYBOARD
[  1310.233] (II) Initializing extension XC-MISC
[  1310.233] (II) Initializing extension SECURITY
[  1310.233] (II) Initializing extension XFIXES
[  1310.233] (II) Initializing extension RENDER
[  1310.233] (II) Initializing extension RANDR
[  1310.234] (II) Initializing extension COMPOSITE
[  1310.234] (II) Initializing extension DAMAGE
[  1310.234] (II) Initializing extension MIT-SCREEN-SAVER
[  1310.234] (II) Initializing extension DOUBLE-BUFFER
[  1310.234] (II) Initializing extension RECORD
[  1310.234] (II) Initializing extension DPMS
[  1310.235] (II) Initializing extension Present
[  1310.235] (II) Initializing extension DRI3
[  1310.235] (II) Initializing extension X-Resource
[  1310.235] (II) Initializing extension XVideo
[  1310.235] (II) Initializing extension XVideo-MotionCompensation
[  1310.235] (II) Initializing extension SELinux
[  1310.235] (II) SELinux: Disabled on system
[  1310.235] (II) Initializing extension GLX
[  1310.235] (II) AIGLX: Screen 0 is not DRI2 capable
[  1310.241] (II) IGLX: Loaded and initialized swrast
[  1310.241] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  1310.241] (II) Initializing extension XFree86-VidModeExtension
[  1310.241] (II) Initializing extension XFree86-DGA
[  1310.241] (II) Initializing extension XFree86-DRI
[  1310.241] (II) Initializing extension DRI2
[  1310.243] (II) modeset(0): Damage tracking initialized
[  1310.243] (II) modeset(0): Setting screen physical size to 508 x 285
[  1310.311] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  1310.311] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[  1310.311] (II) LoadModule: "libinput"
[  1310.312] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[  1310.314] (II) Module libinput: vendor="X.Org Foundation"
[  1310.314]     compiled for 1.21.1.11, module version = 1.4.0
[  1310.314]     Module class: X.Org XInput Driver
[  1310.314]     ABI class: X.Org XInput driver, version 24.4
[  1310.314] (II) Using input driver 'libinput' for 'Power Button'
[  1310.315] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 22 paused 0
[  1310.315] (**) Power Button: always reports core events
[  1310.315] (**) Option "Device" "/dev/input/event2"
[  1310.318] (II) event2  - Power Button: is tagged by udev as: Keyboard
[  1310.318] (II) event2  - Power Button: device is a keyboard
[  1310.318] (II) event2  - Power Button: device removed
[  1310.319] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  1310.319] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1310.319] (**) Option "xkb_model" "pc105"
[  1310.319] (**) Option "xkb_layout" "us"
[  1310.320] (II) event2  - Power Button: is tagged by udev as: Keyboard
[  1310.320] (II) event2  - Power Button: device is a keyboard
[  1310.321] (II) config/udev: Adding input device Asus Wireless Radio Control (/dev/input/event9)
[  1310.321] (**) Asus Wireless Radio Control: Applying InputClass "libinput keyboard catchall"
[  1310.321] (II) Using input driver 'libinput' for 'Asus Wireless Radio Control'
[  1310.322] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 25 paused 0
[  1310.322] (**) Asus Wireless Radio Control: always reports core events
[  1310.322] (**) Option "Device" "/dev/input/event9"
[  1310.323] (II) event9  - Asus Wireless Radio Control: is tagged by udev as: Keyboard
[  1310.323] (II) event9  - Asus Wireless Radio Control: device is a keyboard
[  1310.323] (II) event9  - Asus Wireless Radio Control: device removed
[  1310.323] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/ATK4002:00/input/input9/event9"
[  1310.323] (II) XINPUT: Adding extended input device "Asus Wireless Radio Control" (type: KEYBOARD, id 7)
[  1310.323] (**) Option "xkb_model" "pc105"
[  1310.323] (**) Option "xkb_layout" "us"
[  1310.325] (II) event9  - Asus Wireless Radio Control: is tagged by udev as: Keyboard
[  1310.325] (II) event9  - Asus Wireless Radio Control: device is a keyboard
[  1310.326] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  1310.326] (II) No input driver specified, ignoring this device.
[  1310.326] (II) This device may have been added with another device file.
[  1310.327] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  1310.327] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[  1310.327] (II) Using input driver 'libinput' for 'Sleep Button'
[  1310.328] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 26 paused 0
[  1310.328] (**) Sleep Button: always reports core events
[  1310.328] (**) Option "Device" "/dev/input/event1"
[  1310.329] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[  1310.330] (II) event1  - Sleep Button: device is a keyboard
[  1310.330] (II) event1  - Sleep Button: device removed
[  1310.330] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  1310.330] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[  1310.330] (**) Option "xkb_model" "pc105"
[  1310.330] (**) Option "xkb_layout" "us"
[  1310.332] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[  1310.332] (II) event1  - Sleep Button: device is a keyboard
[  1310.334] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/event4)
[  1310.334] (**) A4Tech USB Mouse: Applying InputClass "libinput pointer catchall"
[  1310.334] (II) Using input driver 'libinput' for 'A4Tech USB Mouse'
[  1310.386] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 27 paused 0
[  1310.386] (**) A4Tech USB Mouse: always reports core events
[  1310.386] (**) Option "Device" "/dev/input/event4"
[  1310.389] (II) event4  - A4Tech USB Mouse: is tagged by udev as: Mouse
[  1310.389] (II) event4  - A4Tech USB Mouse: device is a pointer
[  1310.389] (II) event4  - A4Tech USB Mouse: device removed
[  1310.390] (II) libinput: A4Tech USB Mouse: Step value 0 was provided, libinput Fallback acceleration function is used.
[  1310.390] (II) libinput: A4Tech USB Mouse: Step value 0 was provided, libinput Fallback acceleration function is used.
[  1310.390] (II) libinput: A4Tech USB Mouse: Step value 0 was provided, libinput Fallback acceleration function is used.
[  1310.390] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:09DA:C10A.0001/input/input4/event4"
[  1310.390] (II) XINPUT: Adding extended input device "A4Tech USB Mouse" (type: MOUSE, id 9)
[  1310.390] (**) Option "AccelerationScheme" "none"
[  1310.390] (**) A4Tech USB Mouse: (accel) selected scheme none/0
[  1310.390] (**) A4Tech USB Mouse: (accel) acceleration factor: 2.000
[  1310.390] (**) A4Tech USB Mouse: (accel) acceleration threshold: 4
[  1310.392] (II) event4  - A4Tech USB Mouse: is tagged by udev as: Mouse
[  1310.393] (II) event4  - A4Tech USB Mouse: device is a pointer
[  1310.394] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/mouse0)
[  1310.394] (II) No input driver specified, ignoring this device.
[  1310.394] (II) This device may have been added with another device file.
[  1310.396] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/event5)
[  1310.396] (II) No input driver specified, ignoring this device.
[  1310.396] (II) This device may have been added with another device file.
[  1310.397] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event6)
[  1310.397] (**) HID 04f3:0103: Applying InputClass "libinput keyboard catchall"
[  1310.397] (II) Using input driver 'libinput' for 'HID 04f3:0103'
[  1310.398] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 28 paused 0
[  1310.398] (**) HID 04f3:0103: always reports core events
[  1310.398] (**) Option "Device" "/dev/input/event6"
[  1310.400] (II) event6  - HID 04f3:0103: is tagged by udev as: Keyboard
[  1310.401] (II) event6  - HID 04f3:0103: device is a keyboard
[  1310.401] (II) event6  - HID 04f3:0103: device removed
[  1310.401] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04F3:0103.0002/input/input6/event6"
[  1310.401] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 10)
[  1310.401] (**) Option "xkb_model" "pc105"
[  1310.401] (**) Option "xkb_layout" "us"
[  1310.403] (II) event6  - HID 04f3:0103: is tagged by udev as: Keyboard
[  1310.403] (II) event6  - HID 04f3:0103: device is a keyboard
[  1310.405] (II) config/udev: Adding input device HID 04f3:0103 Consumer Control (/dev/input/event7)
[  1310.405] (**) HID 04f3:0103 Consumer Control: Applying InputClass "libinput keyboard catchall"
[  1310.405] (II) Using input driver 'libinput' for 'HID 04f3:0103 Consumer Control'
[  1310.406] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 29 paused 0
[  1310.406] (**) HID 04f3:0103 Consumer Control: always reports core events
[  1310.406] (**) Option "Device" "/dev/input/event7"
[  1310.409] (II) event7  - HID 04f3:0103 Consumer Control: is tagged by udev as: Keyboard
[  1310.409] (II) event7  - HID 04f3:0103 Consumer Control: device is a keyboard
[  1310.409] (II) event7  - HID 04f3:0103 Consumer Control: device removed
[  1310.409] (II) libinput: HID 04f3:0103 Consumer Control: needs a virtual subdevice
[  1310.409] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04F3:0103.0003/input/input7/event7"
[  1310.409] (II) XINPUT: Adding extended input device "HID 04f3:0103 Consumer Control" (type: MOUSE, id 11)
[  1310.409] (**) Option "AccelerationScheme" "none"
[  1310.409] (**) HID 04f3:0103 Consumer Control: (accel) selected scheme none/0
[  1310.409] (**) HID 04f3:0103 Consumer Control: (accel) acceleration factor: 2.000
[  1310.409] (**) HID 04f3:0103 Consumer Control: (accel) acceleration threshold: 4
[  1310.412] (II) event7  - HID 04f3:0103 Consumer Control: is tagged by udev as: Keyboard
[  1310.412] (II) event7  - HID 04f3:0103 Consumer Control: device is a keyboard
[  1310.413] (II) config/udev: Adding input device HID 04f3:0103 System Control (/dev/input/event8)
[  1310.413] (**) HID 04f3:0103 System Control: Applying InputClass "libinput keyboard catchall"
[  1310.413] (II) Using input driver 'libinput' for 'HID 04f3:0103 System Control'
[  1310.414] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 30 paused 0
[  1310.414] (**) HID 04f3:0103 System Control: always reports core events
[  1310.414] (**) Option "Device" "/dev/input/event8"
[  1310.417] (II) event8  - HID 04f3:0103 System Control: is tagged by udev as: Keyboard
[  1310.417] (II) event8  - HID 04f3:0103 System Control: device is a keyboard
[  1310.417] (II) event8  - HID 04f3:0103 System Control: device removed
[  1310.417] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04F3:0103.0003/input/input8/event8"
[  1310.417] (II) XINPUT: Adding extended input device "HID 04f3:0103 System Control" (type: KEYBOARD, id 12)
[  1310.417] (**) Option "xkb_model" "pc105"
[  1310.417] (**) Option "xkb_layout" "us"
[  1310.419] (II) event8  - HID 04f3:0103 System Control: is tagged by udev as: Keyboard
[  1310.419] (II) event8  - HID 04f3:0103 System Control: device is a keyboard
[  1310.421] (II) config/udev: Adding input device Elan Touchpad (/dev/input/event10)
[  1310.421] (**) Elan Touchpad: Applying InputClass "libinput touchpad catchall"
[  1310.421] (II) Using input driver 'libinput' for 'Elan Touchpad'
[  1310.422] (II) systemd-logind: got fd for /dev/input/event10 13:74 fd 31 paused 0
[  1310.422] (**) Elan Touchpad: always reports core events
[  1310.422] (**) Option "Device" "/dev/input/event10"
[  1310.423] (II) event10 - Elan Touchpad: is tagged by udev as: Touchpad
[  1310.425] (II) event10 - Elan Touchpad: device is a touchpad
[  1310.425] (II) event10 - Elan Touchpad: device removed
[  1310.425] (II) libinput: Elan Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
[  1310.425] (II) libinput: Elan Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
[  1310.425] (II) libinput: Elan Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
[  1310.426] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN1000:00/input/input10/event10"
[  1310.426] (II) XINPUT: Adding extended input device "Elan Touchpad" (type: TOUCHPAD, id 13)
[  1310.427] (**) Option "AccelerationScheme" "none"
[  1310.427] (**) Elan Touchpad: (accel) selected scheme none/0
[  1310.427] (**) Elan Touchpad: (accel) acceleration factor: 2.000
[  1310.427] (**) Elan Touchpad: (accel) acceleration threshold: 4
[  1310.429] (II) event10 - Elan Touchpad: is tagged by udev as: Touchpad
[  1310.430] (II) event10 - Elan Touchpad: device is a touchpad
[  1310.431] (II) config/udev: Adding input device Elan Touchpad (/dev/input/mouse1)
[  1310.431] (II) No input driver specified, ignoring this device.
[  1310.431] (II) This device may have been added with another device file.
[  1310.432] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[  1310.432] (II) No input driver specified, ignoring this device.
[  1310.432] (II) This device may have been added with another device file.
[  1310.432] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[  1310.432] (II) No input driver specified, ignoring this device.
[  1310.432] (II) This device may have been added with another device file.
[  1310.433] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event11)
[  1310.433] (**) Asus WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[  1310.433] (II) Using input driver 'libinput' for 'Asus WMI hotkeys'
[  1310.434] (II) systemd-logind: got fd for /dev/input/event11 13:75 fd 32 paused 0
[  1310.434] (**) Asus WMI hotkeys: always reports core events
[  1310.434] (**) Option "Device" "/dev/input/event11"
[  1310.435] (II) event11 - Asus WMI hotkeys: is tagged by udev as: Keyboard
[  1310.435] (II) event11 - Asus WMI hotkeys: device is a keyboard
[  1310.435] (II) event11 - Asus WMI hotkeys: device removed
[  1310.435] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input11/event11"
[  1310.435] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 14)
[  1310.435] (**) Option "xkb_model" "pc105"
[  1310.435] (**) Option "xkb_layout" "us"
[  1310.436] (II) event11 - Asus WMI hotkeys: is tagged by udev as: Keyboard
[  1310.436] (II) event11 - Asus WMI hotkeys: device is a keyboard
[  1310.437] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  1310.437] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[  1310.437] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[  1310.438] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 33 paused 0
[  1310.438] (**) AT Translated Set 2 keyboard: always reports core events
[  1310.438] (**) Option "Device" "/dev/input/event3"
[  1310.439] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[  1310.440] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[  1310.440] (II) event3  - AT Translated Set 2 keyboard: device removed
[  1310.440] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  1310.440] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 15)
[  1310.440] (**) Option "xkb_model" "pc105"
[  1310.440] (**) Option "xkb_layout" "us"
[  1310.442] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[  1310.442] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[  1310.454] (**) HID 04f3:0103 Consumer Control: Applying InputClass "libinput keyboard catchall"
[  1310.454] (II) Using input driver 'libinput' for 'HID 04f3:0103 Consumer Control'
[  1310.454] (II) systemd-logind: returning pre-existing fd for /dev/input/event7 13:71
[  1310.454] (**) HID 04f3:0103 Consumer Control: always reports core events
[  1310.454] (**) Option "Device" "/dev/input/event7"
[  1310.454] (II) libinput: HID 04f3:0103 Consumer Control: is a virtual subdevice
[  1310.454] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04F3:0103.0003/input/input7/event7"
[  1310.454] (II) XINPUT: Adding extended input device "HID 04f3:0103 Consumer Control" (type: KEYBOARD, id 16)
[  1310.454] (**) Option "xkb_model" "pc105"
[  1310.454] (**) Option "xkb_layout" "us"
[/HTML]

[HR][/HR]
Just a minor note about this log, I logged out from wayland, and logged back into X11 right after, and then took the logs. For some reason X11, gives me a blank screen upon login (even though it's in recovery mode), after a few days. So I have to switch back to Wayland. Not sure why that happens only to X11 either.
[INDENT]
Best;
[/INDENT]

---

### Post by Bashing-om on 2024-10-09
xashyar; Ouch
> 
(WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
(EE) open /dev/fb0: Permission denied


Related to nomodeset in use ??? Just do not know -
However, let's get around using nomodeset (recovery console) to boot.

try:
Boot to grub's boot menu
At the grub menu press 'e' to edit -
Replace quiet splash with the boot parameter systemd.unit=multi-user.target in the line that starts with linux.
Key combo ctl+x to continue to a TTY.
Here we completely disable starting X on startup.

Now let's start the GUI and see what errors are given:
```

sudo systemctl start graphical.target

```

does the GUI start ?

[INDENT]poking and stroking[/INDENT]

---

### Post by xashyar on 2024-10-10
Bashing-om; 

Unfortunately it doesn't reach the TTY, so I can enter the _systemctl start graphical.target_ command.

I added the _systemd.unit=multi-user.target_ boot parameters (both via grub editor, and editing the etc/default/grub file into: GRUB_CMDLINE_LINUX_DEFAULT="systemd.unit=multi-user.target"

But it boots pretty much with the same behavior as before.

Here's the screen I get after Ctrl+x:
[https://ibb.co/J3YxY74](https://ibb.co/J3YxY74)

> Related to nomodeset in use ??? Just do not know -

Also with regard to this, I still see this in the xorg log, even after I have removed the nomodeset parameter:

[HTML][    29.466] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    29.466] (II) modeset(0): Creating default Display subsection in Screen section[/HTML]

---

### Post by Bashing-om on 2024-10-10
xashyar - Yuk

Makes no sense to me that you can not reach a TTY from grub - EFI can not direct to the initramfs ?? Huh ! We know that it does when booting with the "nomodeset" parameter.

Will scratch my head a spell -- and run around in more circles.
Will return when I have something constructive to add.

[INDENT]hate when this happens
[/INDENT]

---

### Post by xashyar on 2024-10-12
Bashing-om; Fingers crossed!

Just to be sure;
> Makes no sense to me that you can not reach a TTY from grub - EFI can  not direct to the initramfs ?? Huh ! We know that it does when booting  with the "nomodeset" parameter.

The only way I can get to the TTY from grub, is with the "recovery" parameter, "nomodeset" doesn't make any difference.

[INDENT]Best!
[/INDENT]

---

### Post by Bashing-om on 2024-10-12
xashyar; Me thinks

"recovery" does employ nomodeset to boot.

Possible that you are not following my advise to boot from grub's boot menu.

Boot to the grub menu
and with the latest kernel (default) selected; press the e key for edit mode.
In this next screen is the boot sequence - arrow down to the line that starts with linux
substitute systemd.unit=multi-user.target for quiet splash
key combo ctl+x to continue to boot

do you now boot to a TTY ?

[INDENT]maybe Yes
[/INDENT]

---

### Post by xashyar on 2024-10-12
Bashing-om; Ooops!

Sorry I described it badly.

This is exactly what happens.

1. In the grub menu I edit the first option (Ubuntu):
[https://ibb.co/mJtzFWt](https://ibb.co/mJtzFWt)
[IMG]https://ibb.co/4RqjdPz[/IMG]

2. And, as usual this is what happens when I press Ctrl + X:
[https://ibb.co/myhGbmB](https://ibb.co/myhGbmB)

(But If I pick one of the 'recovery mode' kernels, place 'systemd.unit=multi-user.target' and then press ctrl+x to continue I do get a TTY, to start a graphical.target and the rest)
[INDENT]My digression (°&#8211;°)&#65417; 
[/INDENT]

---

### Post by Bashing-om on 2024-10-12
xashyar - Hey !

A Image *is* worth a thousand words --- 
crashkernel ??
rebooting now and rechecking my memory what the linux line should be !

-I shall return-

---

### Post by Bashing-om on 2024-10-13
xashyar - OK

No idea of the why or wherfore a crashkernel parameter is extent!
All that required ls vmlinuz<version> and the root=UUIDXXXX ro
that boots to the display manger's login screen.
Now we want to boot to a TTY instead so we insert the systemd.unit=multi-user.target parameter.
so:
On the linux line remove all after the root=UUID=<217ed9a7-e11a-4e32-8c05-992e8c8932b6> ro
and next insert that boot parameter systemd.unit=multi-user.target after "ro".
key combo ctl+X

-Now do you boot to a TTY ?

-Maybe-

---

### Post by xashyar on 2024-10-17
Bashing-om; excuse my delayed response.

I removed the crashkernel parameter altogether, and grub's now looking like this:
[https://ibb.co/SVgMKVr](https://ibb.co/SVgMKVr)

But unfortunately I still get the boot-freeze scenario, after hitting ctrl+x:
[https://ibb.co/GTWth0J](https://ibb.co/GTWth0J)


Also, I think this bug is very similar:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-535/+bug/2031198](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-535/+bug/2031198)

---

### Post by Bashing-om on 2024-10-18
xashyar - Sorry

Now above my skills set.
Unable to boot to a TTY and I can not explain why :(

Looks as Daniel van Vugt (vanvugt) - very talented developer - from the bug report; seems to indicate there is no real fix here.

ouch!

---

### Post by xashyar on 2024-10-20
Bashing-om; It is kind of sad,

Yess Daniel also chimed in on my bug report [https://bugs.launchpad.net/ubuntu/+bug/2071680](https://bugs.launchpad.net/ubuntu/+bug/2071680) and marked it as inconclusive.

The truth of it is, I used to run Ubuntu on this machine for a long time, pre-2022, and now in 2024. My hunch was that something has changed in this period and therefore we can trace it, hopefully. :)


I have a few options left now, 1) Try a non-GNOME Ubuntu flavor (perhaps Kubuntu?), however I'm not sure if it's a DE problem. 2) Downgrading the BIOS/UEFI firmware, not sure a good idea, but I can try 3) Trying Debian, since it's a more conservative release, 4) Wait for a new Nvidia-driver release

And eventually if all fails, I might have to bite the actual bullet and go back to windows, it's real hard to deal with Ubuntu in recovery mode.[INDENT]Best
[/INDENT]

---

