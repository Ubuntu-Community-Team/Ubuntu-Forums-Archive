---
title: "Surface Pro 3 hangs on grub screen after shim update if any peripherals attached"
date: 2021-07-29
forum: Hardware
---

### Post by rbrdvr on 2021-07-29
After  installing shim update (shim-signed:amd64 1.48+15.4-0ubuntu5)  Surface  Pro 3 running Kubuntu 21.04 (kernel 5.11.0.25-generic), hangs  on boot  during grub screen if _any_ peripherals attached. It could be a  usb hub  with nothing connected to it or an external display connected  via mini displayport. System  boots fine if nothing is attached.

shim-signed:amd64 1.50+15.4-0ubuntu7 (latest update afaik) didn't fix the issue

It appears Surface Pro only issue, I don't have the same problem with  other computers running the same version of os with the same updates.
How do I fix it?

---

### Post by rbrdvr on 2021-07-31
some additional observations:

1. sometimes system doesn't hang/freeze up
2. disabling secure boot doesn't affect the behavior, system may still hang before kernel is loaded with peripherals attached
    it does seem to be a bit "easier" to make system lock up with secure boot enabled, but still happens with it disabled
3. sometimes system hangs before grub screen is loaded, on power up, while displaying "Surface" logo
4. adding more connected things increases probability of system freezing, for example Microsoft's Surface Dock that also provides power, or Microsoft power adapter
5. adding another peripheral during grub timeout may hang the system - this one is the one that was the easiest to replicate
6. once the grub screen is gone and kernel is loading or loaded, I can add as many peripherals as I have available and system doesn't hang

so, to sum up:

system is unstable (hangs) _only_ during grub if peripherials are attached
enabling or disabling secure boot makes no difference

once the grub is done, i can attach all the same things that hang the system during grub with no problem
none of this behavior was ever observed before the shim update


question:

is there a way to enable any debug log in grub2 and have it write to the efi partition? my root is btrfs and it doesn't look like grub2 can write to it.
or, how to I enable debug output on the screen?

---

### Post by rbrdvr on 2021-08-03
ended up reinstalling kubuntu 21.04. It's "fixed" now. I do still have a question, see below:

interestingly,  if Secure boot is enabled and I'm allowing the installer to download  updates during installation, i get an error related to shim-signed:
"installed shim-signed package post-installation script subprocess returned error exit status 1" and installation fails

the  only way I was able to avoid getting this error - disable secure boot,  install everything, then enable secure boot. now I'm not sure if correct  keys are enrolled into the uefi and that i have protection expected  from secure boot.
Do I?

---

### Post by tea for one on 2021-08-03
If the correct keys are not enrolled after re-enabling secure boot, then the UEFI firmware implementation is at fault.
I would expect the same protection as if secure boot had remained enabled.
Does your UEFI firmware have a setting to reset the security keys to default?

As your PC is a Microsoft device and Microsoft were very keen to insist on secure boot (especially for upcoming Windows 11), it would be very negligent of them to cause any difficulty when secure boot is disabled/enabled.

The question [COLOR="#0000FF"]Do you trust the users who have access to the PC?[/COLOR] may be more important than the implementation of security software ;).

---

