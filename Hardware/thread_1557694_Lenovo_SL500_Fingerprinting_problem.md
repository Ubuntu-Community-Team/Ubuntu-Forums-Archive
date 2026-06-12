---
title: "Lenovo SL500 Fingerprinting problem"
date: 2010-08-21
forum: Hardware
---

### Post by x2dz on 2010-08-21
Hi everyone,

  I have a Lenovo SL500 machine, which of course boots Ubuntu Lucid 32-bit /Netbook edition/ ;)

  The problem is the fingerprinting device /from lsusb/ - 
```
Bus 005 Device 003: ID 147e:1000 Upek
```

  I managed to get it working and somewhat working (recognized as unknown device/vendor in GUI) via Fingerprint GUI. I followed the step-by-step.pdf supplied in the package. When i issue "sudo fingerprint-gui" the program starts and all is well - the program uses the device OK, but then the saved fingerprint are saved for root. If I try and start it as a normal user at the moment of scanning I get - ERROR -> Could not open fingerprint device. Permission problem?

And this is what I get in /var/log/auth.log -> 
```
Aug 21 10:34:17 x2dz fingerprint-gui[4462]: ABSOpen() failed -1086 (An internal error occurred (pt: tfmerr -1086).).
Aug 21 10:34:17 x2dz fingerprint-gui[4462]: No device open.
```

I tried following some guides I found online stating the same problem /including chmodding the usb device and changing the rule order/, but none of them seemed to do anything to even change the error.

I should also mention that I enabled su login via fingerprint /for root/ which should theoretically work, even with the permission problem, but this is what happens when I type su in the terminal -   
```
x2dz@x2dz:~$ su
Password: 
This process is currently running setuid or setgid.
GTK+ does not allow this therefore Qt cannot use the GTK+ integration.
Try launching your app using 'gksudo', 'kdesudo' or a similar tool.

See http://www.gtk.org/setuid.html for more information.


Password: 
su: Permission denied

```

When I get the first password line the fingerprint authentication GUI appears and it says "Authenticating Root" at the bottom.,rs... At this point I should be logged in as Root... but then I get the second password line just sitting there. The stuff about setuid and setgid is written as soon as the fingerprint authentication GUI is shown... BTW, even if I enter as password with the keyboard, regardless of what I enter, I get access denied.

This is what I get in auth.log

```
Aug 21 11:14:00 x2dz su[4666]: PAM pam_parse: expecting return value; [...sufficent]
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Got "debug" argument.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Got no PAM_RHOST.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Got no SSH_CONNECTION.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Got no PAM_AUTHTOK.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: PAM_SERVICE: su.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: PAM_TTY: /dev/pts/1.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Have PAM user root.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Have display=:0.0, XAUTHORITY=/var/run/gdm/auth-for-x2dz-yAqaJq/database.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Parent PID: 4666.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Child PID: 4668.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Wrote random string to fifo.
Aug 21 11:14:00 x2dz pam_fingerprint-gui[4666]: Prompting "Password: "
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Got "debug" argument.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Have username root.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Started.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg0: fingerprint-helper.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg1: 3.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg2: -d.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg3: -u.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg4: root.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg5: dUmMy4.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Arg6: dUmMy5.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Have pipe 3.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Wrote pidfile /tmp/fingerprint-helper.pid.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Proprietary lib "libbsapi.so" loaded.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Libfprint initialized.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Libbsapi initialized.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Found USB device: unknown vendor/unknown device.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: last message repeated 11 times
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Have libbsapi-device mid01,usb,device=#01VID_147e_PID_1000_BCD_0033_BUS_005:01.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: initializing libbsapi device (vend/prod) 0x147e/0x1000
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Added libbsapi.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Current device set to 0 -- libbsapi.
Aug 21 11:14:01 x2dz fingerprint-helper[4668]: Discovered device: libbsapi.
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Device can identify.
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Have display=:0.0, XAUTHORITY=/var/run/gdm/auth-for-x2dz-yAqaJq/database.
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Authenticating USER: root
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Identifying all discovered fingerprints from root.
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Have X-display :0.0. Starting GUI authentication.
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Message: Authenticating root
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Could not open named pipe (fingerprint-plugin not present).
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: Starting identify.
Aug 21 11:14:02 x2dz fingerprint-helper[4668]: ABS_MSG_PROMPT_SCAN.
Aug 21 11:14:04 x2dz fingerprint-helper[4668]: ABS_MSG_PROCESS_SUCCESS.
Aug 21 11:14:04 x2dz fingerprint-helper[4668]: last message repeated 2 times
Aug 21 11:14:04 x2dz fingerprint-helper[4668]: Thread ended normally.
Aug 21 11:14:04 x2dz fingerprint-helper[4668]: Message: OK
Aug 21 11:14:04 x2dz fingerprint-helper[4668]: Could not open named pipe (fingerprint-plugin not present).
Aug 21 11:14:06 x2dz fingerprint-helper[4668]: Using libfakekey to exit PAM conversation (1976977565).
Aug 21 11:14:06 x2dz fingerprint-helper[4668]: Fingerprint recognized, EXIT_SUCCESS.
Aug 21 11:14:06 x2dz fingerprint-helper[4668]: Could not open named pipe (fingerprint-plugin not present).
Aug 21 11:14:06 x2dz pam_fingerprint-gui[4666]: Checking for encrypted homedir "/root".
Aug 21 11:14:06 x2dz pam_fingerprint-gui[4666]: File "/root/README.txt" doesn't exist; assuming not encrypted.
Aug 21 11:14:06 x2dz pam_fingerprint-gui[4666]: Return 0 (PAM_SUCCESS).
Aug 21 11:14:06 x2dz pam_fingerprint-gui[4666]: Could not open named pipe (fingerprint-plugin not present).
Aug 21 11:14:08 x2dz su[4666]: pam_unix(su:auth): authentication failure; logname=x2dz uid=1000 euid=0 tty=/dev/pts/1 ruser=x2dz rhost=  user=root
Aug 21 11:14:10 x2dz su[4666]: pam_authenticate: Permission denied
Aug 21 11:14:10 x2dz su[4666]: FAILED su for root by x2dz
Aug 21 11:14:10 x2dz su[4666]: - /dev/pts/1 x2dz:root

```

Sorry, it was even longer, but i truncated some non-essential parts.

I would be extremely greatful if anyone could be able to help me get this working... I assume its something dreadfully trivial, but I can't put my finger on it...

So thanks in advance!

---

### Post by x2dz on 2010-08-25
Anyone??

Getting desperate :(

---

### Post by x2dz on 2010-10-27
I still haven't managed to find anything on how to get this working...


Anyone.... please?

---

