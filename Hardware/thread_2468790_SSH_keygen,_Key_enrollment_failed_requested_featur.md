---
title: "SSH keygen, Key enrollment failed: requested feature not supported"
date: 2021-11-10
forum: Hardware
---

### Post by isprins on 2021-11-10
Hello, I have issues generating ed25519 keys on my yubikey 5 NFC.
I have collected the relevant information:

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 21.10
Release:	21.10
Codename:	impish

uname -r
5.13.0-21-generic

ssh -V 
OpenSSH_8.4p1 Ubuntu-6ubuntu2, OpenSSL 1.1.1l  24 Aug 2021

Dmesg output:
21.960057] usb 1-3: new full-speed USB device number 4 using xhci_hcd
[   22.296859] usb 1-3: New USB device found, idVendor=1050, idProduct=0407, bcdDevice= 5.12
[   22.296869] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   22.296873] usb 1-3: Product: YubiKey OTP+FIDO+CCID
[   22.296876] usb 1-3: Manufacturer: Yubico
[   22.296879] usb 1-3: SerialNumber: 0009031500
[   22.331164] input: Yubico YubiKey OTP+FIDO+CCID as /devices/pci0000:00/0000:00:01.3/0000:02:00.0/usb1/1-3/1-3:1.0/0003:1050:0407.0004/input/input19
[   22.388838] hid-generic 0003:1050:0407.0004: input,hidraw3: USB HID v1.10 Keyboard [Yubico YubiKey OTP+FIDO+CCID] on usb-0000:02:00.0-3/input0
[   22.396252] hid-generic 0003:1050:0407.0005: hiddev2,hidraw4: USB HID v1.10 Device [Yubico YubiKey OTP+FIDO+CCID] on usb-0000:02:00.0-3/input1


lsusb -v 2>/dev/null | grep -A2 Yubico | grep "bcdDevice" | awk '{print $2}'
5.12 ( key firmware version )

Tried with they key pin:
ssh-keygen -t ed25519-sk -O resident -vvv
Generating public/private ed25519-sk key pair.
You may need to touch your authenticator to authorize key generation.
Enter PIN for authenticator: 
debug3: start_helper: started pid=2678
debug3: ssh_msg_send: type 5
debug3: ssh_msg_recv entering
debug1: start_helper: starting /usr/lib/openssh/ssh-sk-helper 
debug1: sshsk_enroll: provider "internal", device "(null)", application "ssh:", userid "(null)", flags 0x21, challenge len 0 with-pin
debug1: sshsk_enroll: using random challenge
debug1: sk_probe: 1 device(s) detected
debug1: sk_probe: selecting sk by touch
debug1: ssh_sk_enroll: using device /dev/hidraw4
debug1: ssh_sk_enroll: /dev/hidraw4 does not support credprot, refusing to create unprotected resident/verify-required key
debug1: sshsk_enroll: provider "internal" returned failure -2
debug1: ssh-sk-helper: Enrollment failed: requested feature not supported
debug1: ssh-sk-helper: reply len 8
debug3: ssh_msg_send: type 5
debug1: client_converse: helper returned error -59
debug3: reap_helper: pid=2678
Key enrollment failed: requested feature not supported

Tried with touching the key:
$ ssh-keygen -t ed25519-sk -O resident -vvv
Generating public/private ed25519-sk key pair.
You may need to touch your authenticator to authorize key generation.
Enter PIN for authenticator: 
debug3: start_helper: started pid=2681
debug3: ssh_msg_send: type 5
debug3: ssh_msg_recv entering
debug1: start_helper: starting /usr/lib/openssh/ssh-sk-helper 
debug1: sshsk_enroll: provider "internal", device "(null)", application "ssh:", userid "(null)", flags 0x21, challenge len 0 with-pin
debug1: sshsk_enroll: using random challenge
debug1: sk_probe: 1 device(s) detected
debug1: sk_probe: selecting sk by touch
debug1: ssh_sk_enroll: using device /dev/hidraw4
debug1: ssh_sk_enroll: /dev/hidraw4 does not support credprot, refusing to create unprotected resident/verify-required key
debug1: sshsk_enroll: provider "internal" returned failure -2
debug1: ssh-sk-helper: Enrollment failed: requested feature not supported
debug1: ssh-sk-helper: reply len 8
debug3: ssh_msg_send: type 5
debug1: client_converse: helper returned error -59
debug3: reap_helper: pid=2681
Key enrollment failed: requested feature not supported

Any solutions on this, is this a bug ?

---

### Post by TheFu on 2021-11-10
Does:
```
$ ssh-keygen -t ecdsa-sk -f ~/.ssh/id_ecdsa_sk
```
not work?
[https://developers.yubico.com/SSH/](https://developers.yubico.com/SSH/)

---

### Post by isprins on 2021-11-10
Yes, but thats not resident mode.
 And the link you mentioned is down:
[https://developers.yubico.com/Securing_SSH_with_FIDO2.html](https://developers.yubico.com/Securing_SSH_with_FIDO2.html)

This one works:
[https://www.stavros.io/posts/u2f-fido2-with-ssh/](https://www.stavros.io/posts/u2f-fido2-with-ssh/)
Same issue with ssh-keygen -t ed25519-sk -O resident -f ~/.ssh/id_mykey_sk

I got an answer from yubikey support.
It seems that my keys have firmware that is to old.
 To use residential keys you need to have a YubiKey with credential management, this was added in Firmware 5.2.3 :(

---

