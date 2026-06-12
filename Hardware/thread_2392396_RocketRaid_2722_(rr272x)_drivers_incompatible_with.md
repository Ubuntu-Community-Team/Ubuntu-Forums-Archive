---
title: "RocketRaid 2722 (rr272x) drivers incompatible with 18.04, kernel 4.15 - help"
date: 2018-05-20
forum: Hardware
---

### Post by kxb on 2018-05-20
Hi all -

The latest official drivers, v 1.5.18 [here]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/Linux/RR272x_1x_Linux_Src_v1.5.18_15_04_21.tar.gz") don't support kernel 4.15. 

There are two problems:
1. Somewhere around kernel 4.7, mutex locking changed (or something along those lines).  See this [thread ]("https://ubuntuforums.org/showthread.php?t=1899544&page=10")- the same code exists for the rr272x driver.
2. Kernel timer implementation changed in 4.15

Does anyone out there have an updated driver?  Or, does anyone with some timer knowledge want to have a go at updating the driver?  I think the other change (#1) is trivial to copy from the link I gave - I had a go and made it through with no compile errors for that section.

Thanks
Kris

---

### Post by yurac777 on 2018-09-02
I created a repo [https://bitbucket.org/yurac/rr64x](https://bitbucket.org/yurac/rr64x) with patched rr64x that compiles on Ubuntu 18.04.
I did not test it yet - only passed compilation.
Commit fab35215f93ad866667b6fe0519f11d723c61cc1 tested with Ubuntu 16.04.

Here is the patch:
diff --git a/osm/linux/os_linux.c b/osm/linux/os_linux.c
index d3c3cda..b4070ba 100644
--- a/osm/linux/os_linux.c
+++ b/osm/linux/os_linux.c
@@ -619,9 +619,17 @@ HPT_U8 os_get_vbus_seq(void *osext)
 	return ((PVBUS_EXT)osext)->host->host_no;
 }
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+static void os_timer_for_ldm(struct timer_list *t)
+#else
 static void os_timer_for_ldm(unsigned long data)
+#endif
 {
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+	PVBUS_EXT vbus_ext = from_timer(vbus_ext, t, timer);
+#else
 	PVBUS_EXT vbus_ext = (PVBUS_EXT)data;
+#endif
 	unsigned long flags;
 
 	spin_lock_irqsave(vbus_ext->lock, flags);
@@ -637,7 +645,9 @@ void  os_request_timer(void * osext, HPT_U32 interval)
 	
 	del_timer(&vbus_ext->timer);
 	vbus_ext->timer.function = os_timer_for_ldm;
+#if LINUX_VERSION_CODE < KERNEL_VERSION(4, 15, 0)
 	vbus_ext->timer.data = (unsigned long)vbus_ext;
+#endif
 	vbus_ext->timer.expires = jiffies + 1 + interval / (1000000/HZ);
 	add_timer(&vbus_ext->timer);
 }
diff --git a/osm/linux/osm_linux.c b/osm/linux/osm_linux.c
index 65315d3..ee3a3ae 100644
--- a/osm/linux/osm_linux.c
+++ b/osm/linux/osm_linux.c
@@ -16,6 +16,13 @@ module_param(autorebuild, int, 0);
 MODULE_PARM(autorebuild, "i");
 #endif
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+struct timer_list_ex {
+	struct timer_list t;
+	HPT_UPTR data;
+};
+#endif
+
 /* notifier block to get notified on system shutdown/halt/reboot */
 static int hpt_halt(struct notifier_block *nb, ulong event, void *buf);
 static struct notifier_block hpt_notifier = {
@@ -319,7 +326,11 @@ static int hpt_detect (Scsi_Host_Template *tpnt)
 
 		spin_lock_init(&initlock);
 		vbus_ext->lock = &initlock;
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+		timer_setup(&vbus_ext->timer, 0 ,0);
+#else
 		init_timer(&vbus_ext->timer);
+#endif
 
 		for (hba = vbus_ext->hba_list; hba; hba = hba->next) {
 			if (!hba->ldm_adapter.him->initialize(hba->ldm_adapter.him_handle)) {
@@ -1470,10 +1481,18 @@ static void hpt_flush_done(PCOMMAND pCmd)
 	up(sem);
 }
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+static void cmd_timeout_sem(struct timer_list *tl)
+{
+	struct timer_list_ex *t = (struct timer_list_ex *)tl;
+	up((struct semaphore *)t->data);
+}
+#else
 static void cmd_timeout_sem(unsigned long data)
 {
 	up((struct semaphore *)(HPT_UPTR)data);
 }
+#endif
 
 /*
  * flush a vdev (without retry).
@@ -1482,7 +1501,13 @@ static int hpt_flush_vdev(PVBUS_EXT vbus_ext, PVDEV vd)
 {
 	PCOMMAND pCmd;
 	unsigned long flags, timeout;
-	struct timer_list timer;
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+	struct timer_list_ex timer_s;
+	struct timer_list *timer = &timer_s.t;
+#else
+	struct timer_list timer_s;
+	struct timer_list *timer = &timer_s;
+#endif
 	struct semaphore sem;
 	int result = 0;
 	HPT_UINT count;
@@ -1518,14 +1543,19 @@ wait:
 
 	if (down_trylock(&sem)) {
 		timeout = jiffies + 20 * HZ;
-		init_timer(&timer);
-		timer.expires = timeout;
-		timer.data = (HPT_UPTR)&sem;
-		timer.function = cmd_timeout_sem;
-		add_timer(&timer);
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+		timer_setup(timer, cmd_timeout_sem ,0);
+		timer_s.data = (HPT_UPTR)&sem;
+#else
+		init_timer(timer);
+		timer->data = (HPT_UPTR)&sem;
+		timer->function = cmd_timeout_sem;
+#endif
+		timer->expires = timeout;
+		add_timer(timer);
 		if (down_interruptible(&sem))
 			down(&sem);
-		del_timer(&timer);
+		del_timer(timer);
 	}
 
 	spin_lock_irqsave(vbus_ext->lock, flags);
@@ -1645,15 +1675,29 @@ static void hpt_ioctl_done(struct _IOCTL_ARG *arg)
 	arg->ioctl_cmnd = 0;
 }
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+static void hpt_ioctl_timeout(struct timer_list *tl)
+{
+	struct timer_list_ex *t = (struct timer_list_ex *)tl;
+	up((struct semaphore *)t->data);
+}
+#else
 static void hpt_ioctl_timeout(unsigned long data)
 {
 	up((struct semaphore *)data);
 }
+#endif
 
 void __hpt_do_ioctl(PVBUS_EXT vbus_ext, IOCTL_ARG *ioctl_args)
 {
 	unsigned long flags, timeout;
-	struct timer_list timer;
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+	struct timer_list_ex timer_s;
+	struct timer_list *timer = &timer_s.t;
+#else
+	struct timer_list timer_s;
+	struct timer_list *timer = &timer_s;
+#endif
 	struct semaphore sem;
 
 	if (vbus_ext->needs_refresh
@@ -1678,14 +1722,19 @@ wait:
 
 	if (down_trylock(&sem)) {
 		timeout = jiffies + 20 * HZ;
-		init_timer(&timer);
-		timer.expires = timeout;
-		timer.data = (HPT_UPTR)&sem;
-		timer.function = hpt_ioctl_timeout;
-		add_timer(&timer);
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
+		timer_setup(timer, hpt_ioctl_timeout, 0);
+		timer_s.data = (HPT_UPTR)&sem;
+#else
+		init_timer(timer);
+		timer->data = (HPT_UPTR)&sem;
+		timer->function = hpt_ioctl_timeout;
+#endif
+		timer->expires = timeout;
+		add_timer(timer);
 		if (down_interruptible(&sem))
 			down(&sem);
-		del_timer(&timer);
+		del_timer(timer);
 	}
 
 	spin_lock_irqsave(vbus_ext->lock, flags);
@@ -2194,6 +2243,8 @@ module_exit(exit_this_scsi_driver);
 
 #endif
 
+#if LINUX_VERSION_CODE <= KERNEL_VERSION(4, 15, 0)
 #if LINUX_VERSION_CODE >= KERNEL_VERSION(2,4,10)
 MODULE_LICENSE("Proprietary");
 #endif
+#endif



> **kxb said:**
> Hi all -

The latest official drivers, v 1.5.18 [here]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/Linux/RR272x_1x_Linux_Src_v1.5.18_15_04_21.tar.gz") don't support kernel 4.15. 

There are two problems:
1. Somewhere around kernel 4.7, mutex locking changed (or something along those lines).  See this [thread ]("https://ubuntuforums.org/showthread.php?t=1899544&page=10")- the same code exists for the rr272x driver.
2. Kernel timer implementation changed in 4.15

Does anyone out there have an updated driver?  Or, does anyone with some timer knowledge want to have a go at updating the driver?  I think the other change (#1) is trivial to copy from the link I gave - I had a go and made it through with no compile errors for that section.

Thanks
Kris

---

### Post by kxb on 2018-09-10
Thanks for that. I saw either your patch or someone else's. I will give it a shot and try adapting to the 272x drivers - long time since I did any C coding!

---

### Post by mjh_ca on 2018-09-19
Thank you!  With some very minor adjustments, I applied your patch to the rr278x driver and it appears to be working perfectly.  Driver source code between RocketRaid 2782 and 2722 seems to be almost identical.

---

### Post by Peter_Tiagunov on 2018-09-22
> **mjh_ca said:**
> Thank you!  With some very minor adjustments, I applied your patch to the rr278x driver and it appears to be working perfectly.  Driver source code between RocketRaid 2782 and 2722 seems to be almost identical.
[FONT=arial][SIZE=2][SIZE=2]
It appears HighPoint released driver that supports kernel 4.15 [http://www.highpoint-tech.com/USA_new/series_rr272x_configuration.htm](http://www.highpoint-tech.com/USA_new/series_rr272x_configuration.htm)
Unfortunately my attempts to install it on Ubuntu 18.04 [/SIZE][LEFT][COLOR=rgba(0, 0, 0, 0.87)][SIZE=2](4.15.0-34-generic) fails.
Can you provide steps on how apply the patch?[/SIZE]

[SIZE=1][FONT=courier new]petert@UPSILON:~/Downloads/RR272x_1x_Linux_Src_v1.10.1_18_03_02$ sudo ./rr272x_1x-linux-src-v1.10.1-18_03_02.bin
Verifying archive integrity... All good.
Uncompressing RR272x_1x Linux Open Source package installer.......................................................................
Checking and installing required toolchain and utility ...
Found program make (/usr/bin/make)
Found program gcc (/usr/bin/gcc)
Found program perl (/usr/bin/perl)
Found program wget (/usr/bin/wget)
[/FONT][/SIZE][/COLOR][/LEFT][COLOR=#ff0000][LEFT][SIZE=1][FONT=courier new]Failed to build driver rr272x_1x for default boot kernel 4.15.0-34-generic.[/FONT][/SIZE][/LEFT][/COLOR][LEFT][COLOR=rgba(0, 0, 0, 0.87)][SIZE=1][FONT=courier new]
cpio: premature end of archive
cpio: premature end of archive
cpio: premature end of archive
cpio: premature end of archive
petert@UPSILON:~/Downloads/RR272x_1x_Linux_Src_v1.10.1_18_03_02$ 


[/FONT][/SIZE][/COLOR][/LEFT][/SIZE][/FONT][SIZE=1][FONT=courier new] [/FONT][/SIZE]

---

### Post by ulysses768 on 2018-09-29
I have the same problem with the "binary" driver for 2720SGL on a newly installed machine.


From /var/log/hptdrv.log it appears the issue is:

```
FATAL: modpost: GPL-incompatible module rr272x_1x.ko uses GPL-only symbol 'sev_enable_key'
```

You can look for workarounds to that, but I am not sure what the ramifications would be.

---

### Post by kxb on 2018-11-06
I successfully installed this version of the driver on kernel 3.13.0-153-generic, in the 14.04.05 LTS release.  I will try it on 18.04 / 4.15 later this week.

I got the same end of archive error, but was able to go into /usr/share/hptdrv/rr272x_1x/product/rr272x/linux and do a 'make install'.  I rebooted and it worked. I may or may not have some kind of a modprobe set up on boot too, so your mileage may vary, but the module built and I'm now mounting drives.

> **Peter_Tiagunov said:**
> [FONT=arial][SIZE=2][SIZE=2]
It appears HighPoint released driver that supports kernel 4.15 [http://www.highpoint-tech.com/USA_new/series_rr272x_configuration.htm](http://www.highpoint-tech.com/USA_new/series_rr272x_configuration.htm)
Unfortunately my attempts to install it on Ubuntu 18.04 [/SIZE][LEFT][COLOR=rgba(0, 0, 0, 0.87)][SIZE=2](4.15.0-34-generic) fails.
Can you provide steps on how apply the patch?[/SIZE]

[SIZE=1][FONT=courier new]petert@UPSILON:~/Downloads/RR272x_1x_Linux_Src_v1.10.1_18_03_02$ sudo ./rr272x_1x-linux-src-v1.10.1-18_03_02.bin
Verifying archive integrity... All good.
Uncompressing RR272x_1x Linux Open Source package installer.......................................................................
Checking and installing required toolchain and utility ...
Found program make (/usr/bin/make)
Found program gcc (/usr/bin/gcc)
Found program perl (/usr/bin/perl)
Found program wget (/usr/bin/wget)
[/FONT][/SIZE][/COLOR][/LEFT][COLOR=#ff0000][LEFT][SIZE=1][FONT=courier new]Failed to build driver rr272x_1x for default boot kernel 4.15.0-34-generic.[/FONT][/SIZE][/LEFT][/COLOR][LEFT][COLOR=rgba(0, 0, 0, 0.87)][SIZE=1][FONT=courier new]
cpio: premature end of archive
cpio: premature end of archive
cpio: premature end of archive
cpio: premature end of archive
petert@UPSILON:~/Downloads/RR272x_1x_Linux_Src_v1.10.1_18_03_02$ 


[/FONT][/SIZE][/COLOR][/LEFT][/SIZE][/FONT][SIZE=1][FONT=courier new] [/FONT][/SIZE]

---

### Post by kxb on 2018-11-11
I installed a clean 18.04 (Server version) and the driver install worked without a hitch.


> **kxb said:**
> I successfully installed this version of the driver on kernel 3.13.0-153-generic, in the 14.04.05 LTS release.  I will try it on 18.04 / 4.15 later this week.

I got the same end of archive error, but was able to go into /usr/share/hptdrv/rr272x_1x/product/rr272x/linux and do a 'make install'.  I rebooted and it worked. I may or may not have some kind of a modprobe set up on boot too, so your mileage may vary, but the module built and I'm now mounting drives.

---

### Post by Knut_Randa on 2019-04-27
@yurac777 I tried to apply your patch but still get errors. My drivers  were updated earlier according to this guide  [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

```
knut@puter:~/rr2340-linux-src-v1.7_modified/product/rr2340/linux$ sudo makemake[1]: Entering directory '/usr/src/linux-headers-4.15.0-48-generic'
  CC [M]  /home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.o
/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.c: In function ‘refresh_sd_flags’:
/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.c:278:41: error: ‘struct gendisk’ has no member named ‘driverfs_dev’
       if (bdev->bd_disk && bdev->bd_disk->driverfs_dev==&SDptr->sdev_gendev) {
                                         ^~
/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.c:283:37: error: ‘struct inode’ has no member named ‘i_mutex’; did you mean ‘i_mode’?
         mutex_lock(&bdev->bd_inode->i_mutex);
                                     ^~~~~~~
                                     i_mode
/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.c:289:39: error: ‘struct inode’ has no member named ‘i_mutex’; did you mean ‘i_mode’?
         mutex_unlock(&bdev->bd_inode->i_mutex);
                                       ^~~~~~~
                                       i_mode
scripts/Makefile.build:330: recipe for target '/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.o' failed
make[2]: *** [/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build/os_linux.o] Error 1
Makefile:1552: recipe for target '_module_/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build' failed
make[1]: *** [_module_/home/knut/rr2340-linux-src-v1.7_modified/product/rr2340/linux/.build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-48-generic'
../../../inc/linux/Makefile.def:107: recipe for target 'rr2340.ko' failed
make: *** [rr2340.ko] Error 2
knut@puter:~/rr2340-linux-src-v1.7_modified/product/rr2340/linux$ 
```

---

### Post by Knut_Randa on 2019-04-27
I figured it out, but now modprobe is acting up.
I have always just done a
```
sudo modprobe rr2340
```
But that now returns
```
modprobe: ERROR: could not insert 'rr2340': Unknown symbol in module, or unknown parameter (see dmesg)
```

Is there more i need to do or did the modprobe command change?

Edit: this last tip in this thread did the trick [https://ubuntuforums.org/showthread.php?t=2404643](https://ubuntuforums.org/showthread.php?t=2404643)

---

### Post by jeremy31 on 2019-04-27
The module is messed up, might be old code

---

### Post by Knut_Randa on 2019-04-27
I am incredibly thankful for this community. Getting the old rocketraid 2340 working again is saving me a fortune. It works perfectly for my use and i don't want to learn a new system. Besides i get to learn a lot about the inner workings of Ubuntu and Linux.

Someone should update the guide for 18.04 though. [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

---

### Post by martini3 on 2020-04-09
I was banging my head against this with RR272x_1x_Linux_Src_v1.10.1_18_03_02 then following the link by xkb above I found a newer driver that works with Ubuntu 18.04
The new driver, RR272x_1x_Linux_Src_v1.10.6_19_12_05 can be found at [https://highpoint-tech.com/USA_new/series_rr272x_configuration.htm](https://highpoint-tech.com/USA_new/series_rr272x_configuration.htm) 
I can confirm that this compiles and works correctly (at least on my system).

---

