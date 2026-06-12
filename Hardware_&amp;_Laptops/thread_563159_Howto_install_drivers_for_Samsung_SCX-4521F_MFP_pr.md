---
title: "Howto install drivers for Samsung SCX-4521F MFP printer/scanner"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by RSkog on 2007-09-29
A while back I managed to get a Samsung SCX-4521F MPF usb printer/scanner to work with Ubuntu Edgy. This may work with other Samsung printers as well. This is what I did:

Download the unified Linux driver from the Samsung web site. This will work with the 20070130094940796_UnifiedLinuxDriver.tar.gz version of the driver.

```
tar -xvzf 20070130094940796_UnifiedLinuxDriver.tar.gz
sudo aptitude install libsane-dev sane sane-utils cups
sudo cp cdroot/Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane
sudo ln -s /usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/libsane-smfp.so.1
sudo cp cdroot/Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
sudo cp cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungspl /usr/lib/cups/filter/
```

The libmfp.so provided with the Samsung driver does a lot ot i/o instructions, accessing the parallel port. This is of course not allowed if you are not root. And we don't want to run the scanning applications as root. I removed a number of i/o instructions from the lib and eventually I got it to run without being root. I have no guarantees for this patch but it works for me.

Note that I assume you are using usb to connect your printer, and thus having no use for the parallel port parts of the printer driver. This will not work if you are using the parallel port to connect you printer.

I tried to replace the i/o instructions with some deterministic code, which hopefully gives the same result everytime it's run. As I said. It works for me.

The patched lib is attached to this post.

```
sudo cp libmfp.so.1.0.1_patched_risk_10mar2007 /usr/lib/libmfp.so.1.0.1

sudo cp cdroot/Linux/i386/lib/libqt-mt.so.3 /usr/lib/
sudo ldconfig

sudo cp cdroot/Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
sudo <your-favorite-editor> /etc/sane.d/dll.conf
```

At the end add:
--- cut cut cut ---
```
smfp
```
--- cut cut cut ---

```
sudo <your-favorite-editor> /etc/udev/rules.d/45-libsane.rules
```

Before LABEL="libsane_rules_end" add:
--- cut cut cut ---
```
# Samsung|SCX-4521F
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="3419", MODE="664", GROUP="scanner"
```
--- cut cut cut ---

```
sudo <your-favorite-editor> /etc/udev/rules.d/60-symlinks.rules
```
At the end, add:
--- cut cut cut ---
```
# Create symlink for usb printer to /dev/usb/lp*
BUS=="usb", KERNEL=="lp[0-9]*", SYMLINK+="usb/%k"
```
--- cut cut cut ---

```
sudo /etc/init.d/udev restart
```

To be able to use the scanner without beeing root you will need access to /dev/usblp0. The easiest way I figured doing this is adding the user(s) to the lp group. I don't know the downsides  to doing this.
```
sudo usermod -a -G lp <user>
```

You will have to log out and back in for the group change to take effect.

With your browser go to: [http://localhost:631/](http://localhost:631/)

This is the cups web interface.

Now, my cups interface is in swedish, so I may not have gotten all the translations exactly as on you screen, You will have to have a little imagination.

Click the "Administration" tab.
Click "Add printer"
Fill out the fields.
Now you have to make sure your printer is turned on and connected to
the USB bus.
Click "Continue"
Select "Samsung SCX-4x21 Series USB #1 (Samsung SCX-4x21 Series)". Note
that selecting "MFP USB Port #0 (SCX-4x21 Series) will not work.
Click "Continue"
Click "Browse" (for PPD-file)
Select "cdroot/Linux/noarch/at_opt/share/ppd/scx4x21.ppd".
Click "Add printer".

You will now have to supply a sudo-capable username and password.

You should now be able to print and scan. (Remember that you have to log
out to join the lp group, to be able to scan.)

Note that if you feel uneasy running the patched lib, you can still use the instructions above (just skip the step copying the patched driver) and printing will work fine for all users. Scanning will only work if you run the scanning application with "sudo".

/Richard

---

### Post by RSkog on 2007-09-29
I forgot to attach the patched driver. Here it is.

/Richard

---

### Post by tiepolo on 2007-11-30
Hello, 

I'm trying to correct the sudo xsane problem and i followed your post, with a scx 4100 and ubuntu feisty - 

I got no result, and i don't find the lp group.

Do you have ideas?

Thanks in advance,

Paolo

---

### Post by hermaf on 2008-05-18
I followed all instructions until the command:

```
sudo <your-favorite-editor> /etc/udev/rules.d/45-libsane.rules
```

In fact I cannot find such file or any libsane.rules file on my system? I am running Ubuntu 8.04 Hardy Heron, could that be an issue?

Thanks
Felix

---

### Post by hermaf on 2008-05-18
> **hermaf said:**
> I am running Ubuntu 8.04 Hardy Heron, could that be an issue?



Seems like Hardy is providing libsane 1.0.19.1ubuntu3 which no longer contains the 45-linsane.rules file. libsane 1.0.18.1ubuntu3 seems the last package containing the file.

---

### Post by hermaf on 2008-05-26
Ok I downgraded the libsane version.

If I start xsane, no scanner is found.

when I do sande-find-scanner I get:

> root@hermaf:/home/hermaf/Desktop# sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

So ... seems that sane-find-scanner discovers my scanner but xsane does not?

---

### Post by hermaf on 2008-05-30
Oh I forgot to mention:
> 
hermaf@hermaf:~/Desktop$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---

### Post by faiper on 2008-07-02
I cant use xsane. 

thiago@desktop:~$ xsane
Falha de segmentação
thiago@desktop:~$ su
Senha: 
root@desktop:/home/thiago# xsane
*** glibc detected *** xsane: double free or corruption (!prev): 0x0823a0d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75b2a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75b64f0]
/usr/lib/libstdc++-libc6.2-2.so.3(__builtin_delete+0x22)[0xb6c4d276]
/usr/lib/libstdc++-libc6.2-2.so.3(__builtin_vec_delete+0x1b)[0xb6c4d29f]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init_mfp_port_control__4port+0x7f)[0xb6c8362b]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init_mfp_port_control__6device+0x16)[0xb6c8411e]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init_mfp_port_control__6driver+0x16)[0xb6c8b002]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(init__C7backendPiPFPCcPcPc_v+0x23)[0xb6c8c77b]
/usr/local/lib/sane/libsane-samsung_scx4x21.so.1(sane_samsung_scx4x21_init+0x31)[0xb6c8cfb1]
/usr/local/lib/libsane.so.1[0xb7f20bbd]
/usr/local/lib/libsane.so.1(sane_dll_get_devices+0x8d)[0xb7f20edd]
/usr/local/lib/libsane.so.1(sane_get_devices+0x24)[0xb7f21444]
xsane[0x80bb282]
xsane[0x80c8a9b]
xsane[0x80c9d38]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb755d450]
xsane[0x804f511]
======= Memory map: ========
08048000-080e3000 r-xp 00000000 08:01 23463      /usr/bin/xsane
080e3000-080e9000 rw-p 0009a000 08:01 23463      /usr/bin/xsane
080e9000-0824f000 rw-p 080e9000 00:00 0          [heap]
b6a00000-b6a21000 rw-p b6a00000 00:00 0 
b6a21000-b6b00000 ---p b6a21000 00:00 0 
b6b5f000-b6c0f000 r-xp 00000000 08:01 158819     /usr/lib/libstdc++.so.5.0.7
b6c0f000-b6c14000 rw-p 000af000 08:01 158819     /usr/lib/libstdc++.so.5.0.7
b6c14000-b6c19000 rw-p b6c14000 00:00 0 
b6c19000-b6c50000 r-xp 00000000 08:01 10727      /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
b6c50000-b6c59000 rw-p 00037000 08:01 10727      /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
b6c59000-b6c5b000 rw-p b6c59000 00:00 0 
b6c5b000-b6c68000 r-xp 00000000 08:01 155734     /usr/lib/libmfp.so.1.0.1
b6c68000-b6c69000 rw-p 0000c000 08:01 155734     /usr/lib/libmfp.so.1.0.1
b6c6c000-b6c6d000 rw-s 00000000 00:09 950298     /SYSVeca8642b (deleted)
b6c6d000-b6c6e000 rw-s 00000000 00:09 917529     /SYSVeca8642a (deleted)
b6c6e000-b6c6f000 rw-s 00000000 00:09 884760     /SYSVeca86429 (deleted)
b6c6f000-b6c70000 rw-s 00000000 00:09 851991     /SYSVeca86428 (deleted)
b6c70000-b6c71000 rw-s 00000000 00:09 819222     /SYSVeca86427 (deleted)
b6c71000-b6c72000 rw-s 00000000 00:09 786453     /SYSVeca86426 (deleted)
b6c72000-b6c73000 rw-s 00000000 00:09 753684     /SYSVeca86425 (deleted)
b6c73000-b6c74000 rw-s 00000000 00:09 720915     /SYSVeca86424 (deleted)
b6c74000-b6c75000 rw-s 00000000 00:09 688146     /SYSVeca86423 (deleted)
b6c75000-b6c76000 rw-s 00000000 00:09 655377     /SYSVeca86422 (deleted)
b6c76000-b6c77000 rw-s 00000000 00:09 622608     /SYSVeca86421 (deleted)
b6c77000-b6c90000 r-xp 00000000 08:01 23679      /usr/local/lib/sane/libsane-samsung_scx4x21.so.1.0.1
b6c90000-b6c94000 rw-p 00018000 08:01 23679      /usr/local/lib/sane/libsane-samsung_scx4x21.so.1.0.1
b6c94000-b6d98000 rw-p b6c94000 00:00 0 
b6d98000-b6e29000 r--p 00000000 08:01 39462      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6e29000-b6e2b000 r-xp 00000000 08:01 16971      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6e2b000-b6e2c000 rw-p 00001000 08:01 16971      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6e2c000-b6e32000 r--s 00000000 08:01 13427      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6e32000-b6e35000 r--s 00000000 08:01 13422      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6e35000-b6e36000 r--s 00000000 08:01 13291      /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6e36000-b6e37000 r--s 00000000 08:01 13290      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6e37000-b6e3a000 r--s 00000000 08:01 13289      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6e3a000-b6e3d000 r--s 00000000 08:01 13285      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6e3d000-b6e40000 r--s 00000000 08:01 13267      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6e40000-b6e48000 r--s 00000000 08:01 11400      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6e48000-b6e50000 r--s 00000000 08:01 11398      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6e50000-b6e51000 r--s 00000000 08:01 10701      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6e51000-b6e54000 r--s 00000000 08:01 10700      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6e54000-b6e5b000 r--s 00000000 08:01 10698      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6e5b000-b6e61000 r--s 00000000 08:01 10688      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6e61000-b6e63000 r--s 00000000 08:01 10667      /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6e63000-b6ec3000 rw-s 00000000 00:09 3473439    /SYSV00000000 (deleted)
b6ec3000-b6ec9000 r-xp 00000000 08:01 47225      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6ec9000-b6eca000 rw-p 00005000 08:01 47225      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6eca000-b6ed4000 r--p 00000000 08:01 72871      /usr/share/locale-langpack/pt_BR/LC_MESSAGES/glib20.mo
b6ed4000-b6eeb000 r--p 00000000 08:01 49407      /usr/share/locale-langpack/pt/LC_MESSAGES/libc.mo
b6eeb000-b6f05000 r--p 00000000 08:01 134442     /usr/share/locale-langpack/pt_BR/LC_MESSAGES/libc.mo
b6f05000-b6f16000 r-xp 00000000 08:01 11627      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6f16000-b6f17000 rw-p 00011000 08:01 11627      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b6f17000-b6f3b000 r--p 00000000 08:01 72608      /usr/share/locale-langpack/pt/LC_MESSAGES/gtk20-properties.mo
b6f3b000-b6f47000 r--p 00000000 08:01 134241     /usr/share/locale-langpack/pt/LC_MESSAGES/xsane.mo
b6f47000-b6f6a000 r--p 00000000 08:01 72799      /usr/share/locale-langpack/pt_BR/LC_MESSAGES/gtk20-properties.mo
b6f6a000-b6f73000 r-xp 00000000 08:01 5950       /lib/tls/i686/cmov/libnss_files-2.7.so
b6f73000-b6f75000 rw-p 00008000 08:01 5950       /lib/tls/i686/cmov/libnss_files-2.7.so
b6f75000-b6f7d000 r-xp 00000000 08:01 5954       /lib/tls/i686/cmov/libnss_nis-2.7.so
b6f7d000-b6f7f000 rw-p 00007000 08:01 5954       /lib/tls/i686/cmov/libnss_nis-2.7.so
b6f7f000-b6f93000 r-xp 00000000 08:01 5944       /lib/tls/i686/cmov/libnsl-2.7.so
b6f93000-b6f95000 rw-p 00013000 08:01 5944       /lib/tls/i686/cmov/libnsl-2.7.so
b6f95000-b6f97000 rw-p b6f95000 00:00 0 
b6f97000-b6f9e000 r-xp 00000000 08:01 5946       /lib/tls/i686/cmov/libnss_compat-2.7.so
b6f9e000-b6fa0000 rw-p 00006000 08:01 5946       /lib/tls/i686/cmov/libnss_compat-2.7.so
b6fa0000-b6fa1000 rw-s 00000000 00:09 589839     /SYSVeca86420 (deleted)
b6fa1000-b6fae000 r--p 00000000 08:01 134302     /usr/share/locale-langpack/pt_BR/LC_MESSAGES/xsane.mo
b6fae000-b6fbe000 r--p 00000000 08:01 72690      /usr/share/locale-langpack/pt/LC_MESSAGES/gtk20.mo
b6fbe000-b6fce000 r--p 00000000 08:01 72868      /usr/share/locale-langpack/pt_BR/LC_MESSAGES/gtk20.mo
b6fce000-b700d000 r--p 00000000 08:01 12232      /usr/lib/locale/pt_BR.utf8/LC_CTYPE
b700d000-b700e000 r--p 00000000 08:01 12380      /usr/lib/locale/pt_BR.utf8/LC_NUMERIC
b700e000-b700f000 r--p 00000000 08:01 15048      /usr/lib/locale/pt_BR.utf8/LC_TIME
b700f000-b70f0000 r--p 00000000 08:01 12231      /usr/lib/locale/pt_BR.utf8/LC_COLLATE
b70f0000-b70f1000 r--p 00000000 08:01 15049      /usr/lib/locale/pt_BR.utf8/LC_MONETARY
b70f1000-b70f4000 rw-p b70f1000 00:00 0 
b70f4000-b70f8000 r-xp 00000000 08:01 8405       /usr/lib/libXdmcp.so.6.0.0
b70f8000-b70f9000 rw-p 00003000 08:01 8405       /usr/lib/libXdmcp.so.6.0.0
b70f9000-b70fb000 r-xp 00000000 08:01 8394       /usr/lib/libXau.so.6.0.0
b70fb000-b70fc000 rw-p 00001000 08:01 8394       /usr/lib/libXau.so.6.0.0
b70fc000-b711b000 r-xp 00000000 08:01 8631       /usr/lib/libexpat.so.1.5.2
b711b000-b711d000 rw-p 0001e000 08:01 8631       /usr/lib/libexpat.so.1.5.2
b711d000-b711e000 rw-p b711d000 00:00 0 
b711e000-b7135000 r-xp 00000000 08:01 183040     /usr/lib/libxcb.so.1.0.0
b7135000-b7136000 rw-p 00016000 08:01 183040     /usr/lib/libxcb.so.1Cancelado

---

