---
title: "Thinkpad sleep power drain solution (ubuntu 8.04)"
date: 2009-02-15
forum: Hardware
---

### Post by panzerkiller on 2009-02-15
Just test OK on my T41 2373-w46, use mobility radeon 9000; it takes me, a pure newbird two days to figure out this, hope it will help someone.

Thinkpad sleep power drain solution (ubuntu 8.04)
Step1: use root account, use test script from thinkwiki to confirm you have this problem;
	code:   #su
		#chmod +x sleep.sh
		#source sleep.sh
		(wait for 20 min, then press power to resume, your screen will seems frozen, acturally it is alive, just type "restart" to restart)
step2:edit /etc/initramfs-tools/modules to add radeonfb module, do not forget to run update-initramfs
	code:	#su
		#gedit modules
		(just add "radeonfb" to a new line, save and exit)
		#update-initramfs -u
		(-u means just update the current kernel, -all will update all)
step3:edit /boot/grub/menu.lst, add "video=radeonfb:force_sleep" at the kernel line.

step4:restart, check if radeonfb is loaded 
	code:	#dmesg | grep radeonfb
		(it will be ok if it display: radeonfb: IBM Thinkpad R50/R51/T40/T41 detected, enabling workaround )	

Do not forget to test again. 
Here is my bettery.log that created by the script:
##################################
2009&#24180; 02&#26376; 15&#26085; &#26143;&#26399;&#26085; 15:50:14 SGT
before: 49490 mWh
after: 48580 mWh
diff: -910 mWh
seconds: 714 sec
result: -4588 mW
Your model seems to be affected.
!!! The notebook was suspended less than 20 minutes.
!!! To get representative values please let the notebook sleep
!!! for at least 20 minutes.

2009&#24180; 02&#26376; 15&#26085; &#26143;&#26399;&#26085; 16:08:40 SGT
before: 46560 mWh
after: 44500 mWh
diff: -2060 mWh
seconds: 1650 sec
result: -4494 mW
Your model seems to be affected.

2009&#24180; 02&#26376; 15&#26085; &#26143;&#26399;&#26085; 16:59:54 SGT
before: 37870 mWh
after: 37610 mWh
diff: -260 mWh
seconds: 1207 sec
################################

---

### Post by panzerkiller on 2009-02-15
the detail info from thinkwiki:
[http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep](http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep)

the script and the usage:
[http://www.thinkwiki.org/wiki/ACPI_sleep_power_drain_test_script](http://www.thinkwiki.org/wiki/ACPI_sleep_power_drain_test_script)

---

