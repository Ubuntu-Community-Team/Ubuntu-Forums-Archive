---
title: "kinit:No resume image, doing normal boot... and other errors in the boot sequence"
date: 2008-07-21
forum: General Help
---

### Post by Crowchild on 2008-07-21
So things are working pretty well for me using Hardy on my Dell XPS M1330 laptop except that when I am booting and shutting down there are a number failed and error messages that flash by. The first one I see is related to: kinit:No resume image, doing normal boot...

I am hoping that someone can show me how to get a readout of all the stuff that flashes by during the boot up and shut down sequences and help me fix some of the errors therein.

Thank you,

Adam

---

### Post by Tim Sharitt on 2008-07-21
If everything works, I wouldn't worry. Messages like that are normal. To see then at boot time hit Ctrl-Alt-F8. I believe 'kinit:No resume image, doing normal boot...' just means there was no session image saved from hibernation.

---

### Post by drs305 on 2008-07-21
Tim may be right that no image is present, but sometimes after partitioning the resume image gets messed up because of a changed UUID. If you are having problems you can compare the UUID number in the cat command with the blkid of the first command. Otherwise that message is not a serious one.
```
sudo blkid | grep swap
cat /etc/initramfs-tools/conf.d/resume

```

If they are different, backup and edit the file and change the UUID to match the blkid result:
```

sudo cp /etc/initramfs-tools/conf.d/resume /etc/initramfs-tools/conf.d/resume-old
gksu gedit /etc/initramfs-tools/conf.d/resume

```

Finally:
```

sudo update-initramfs -u

```

---

### Post by Crowchild on 2008-07-23
So given that I never use this function is there a way that I can kill the process therefore improving my boot time?

Also, is there a better way than trying to read very quickly all the failed or error messages during the boot sequence such as a log file? I am asking because I do have a few error that I can see in there and the boot time is rather long.

Thank you.

---

### Post by drs305 on 2008-07-23
> **Crowchild said:**
> Also, is there a better way than trying to read very quickly all the failed or error messages during the boot sequence such as a log file? I am asking because I do have a few error that I can see in there and the boot time is rather long.

This command can show what happened during boot - the left number is the time starting at 0 seconds. It looks pretty complicated but if you go through it slowly you can make sense out of at least some of it...
```

cat /var/log/dmesg
```

You can add ' | grep XXX ' after the command to search for certain words. Replace XXX with 'fail', 'error', or whatever other word you might want to search for.
Example:
```

cat /var/log/dmesg | grep error
```

---

### Post by Crowchild on 2008-07-24
Alright, Thanks guys now we're getting somewhere...

So far the biggest error is: hub 1-2:1.0: hub_port_status failed (err = -71)

(biggest in the sense that it extends the boot time the longest)

I get this message about three times and then there is a long pause and booting continues.

Still no ideas on how to avoid looking for the resume image?

Also is there a similar command to view the shut down sequence? I see a number of errors there too.



Thanks again, your help is appreciated as you can imagine, it's awfully hard to be an advocate for Ubuntu when the first question is, 'Why is does it take so long to boot?'

---

### Post by chrisccoulson on 2008-07-24
```
kinit:No resume image, doing normal boot...
```
...is not an error. This just means that no resume image was found, so it is doing a normal boot. When you hibernate (suspend-to-disk), the state of your machine is written to your swap partition. When you next boot the machine, a resume image will be found on your swap partition at this step, and this resume image will be used to restore the state of the machine.

If you shut down your machine normally, no image is written to the swap partition, so the kernel finds no resume image on a subsequent boot and then prints this message.

Searching for the resume image only takes a few milli-seconds, and I don't think it is something that you can stop.

The kernel is very verbose during boot-up, and I wouldn't worry about most of the messages you see. Most of these are normal messages and not error messages.

---

### Post by venik212 on 2008-08-02
I get the same: kinit: No resume image stuff, but it never progresses beyond that to kdm.  I did no patyiyioning, so the uuid solution above should not apply.  When I am asked for username, I type my username and password, it does not start the KDM, so no gui is available.  How do I fix that?

---

### Post by chrisccoulson on 2008-08-02
> **venik212 said:**
> I get the same: kinit: No resume image stuff, but it never progresses beyond that to kdm.  I did no patyiyioning, so the uuid solution above should not apply.  When I am asked for username, I type my username and password, it does not start the KDM, so no gui is available.  How do I fix that?

The 'kinit: No resume image' message is not related to your problem of KDM not starting, and it isn't stalling the boot. What you're seeing is your machine successfully boot to a getty on TTY1, which the 'kinit' message had already been printed to earlier in the boot process.

Is there anything in your /var/log/kdm.log?

BTW, I think you can stop the kernel looking for a resume image by passing the 'noresume' option to the kernel from GRUB.

---

### Post by venik212 on 2008-08-09
Thanks.  Why does it do it this way all of a sudden?  How do I recover from it?  I like the resume option, and would not like to prevent kubuntu from resuming under normal circumstances.

---

