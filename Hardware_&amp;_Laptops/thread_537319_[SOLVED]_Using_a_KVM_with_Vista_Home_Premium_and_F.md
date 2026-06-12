---
title: "[SOLVED] Using a KVM with Vista Home Premium and Feisty"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by JawsThemeSwimming428 on 2007-08-28
I have now learned a lesson, when a product has mostly bad reviews, do not buy it. Now that I vented a little let me explain my situation. I recently bought a Velocity Micro ProMagix system with (yuck) Vista Home Premium on it. All in all I can't bad mouth Vista too much yet, it hasn't performed horrible. But, surprisingly, Vista is not my problem. I also have a machine that I built about a year and a half ago that only runs Feisty. The machine has worked near flawlessly since I built it and installed Dapper Drake. I upgraded to Feisty. 
My setup, for the past year and a half is using a KVM for my monitor, keyboard, and mouse to share between the PC's (they were all using PS/2 connections. Well the Velocity Micro machine I bought doesn't have any PS/2 connectors, so I obviously needed to purchase a new KVM. My Samsung SyncMaster 226BW 22" Monitor has two monitor connections so I have the Ubuntu machine hooked up with VGA (because its graphics card isn't as good as the newer one) and the Vista machine is using DVI. I had a lot of difficulty finding a KVM that would allow for the two different monitor connections so I decided for video I would just use the two connections built into the monitor and toggle the video separately. That's fine with me (I'm getting to the issue, sorry).
My Velocity Micro keyboard and Velocity Micro mouse work just fine. I bought a Belkin Flip 2-port USB KVM switch (instead of listening to the reviews), hooked it up, and watched it fail. My Ubuntu machine would not even boot, the Vista machine would boot but whenever I toggled the keyboard/mouse and came back it locked up the machine and there was no bringing it back. Needless to say, I'm done with this piece of crap. But now I am back in the same situation. My Vista machine has the peripherals hooked directly to it and my Feisty machine sits there like an oversized paperweight. I don't want to virtualize my Linux system, so that isn't an option. What I am asking for is someone to give me a solution to using one keyboard and mouse between these two machines. If anyone knows of a USB KVM that does work please let me know. Any ideas on how to solve this issue? Thanks in advance!!

---

### Post by sonofusion82 on 2007-08-28
an alternative is is buy a USB to PS/2 converter so you can still use your old PS/2 KVM.

or, you can just leave the Ubuntu machine without display, keyboard and mouse, just use SSH or VNC to control it from Vista machine or vice versa...

---

### Post by sargentdean on 2007-08-28
> My setup, for the past year and a half is using a KVM for my monitor, keyboard, and mouse to share between the PC's (they were all using PS/2 connections. Well the Velocity Micro machine I bought doesn't have any PS/2 connectors, so I obviously needed to purchase a new KVM.

You_don't_need_a_new_KVM._I_assume_your_new_machine_has_usb_mouse_and_keyboard._If_so_just_buy_a_ps/2_to_usb_adaptor.
That_is_what_I_use_with_my_laptop.

Sarge

Sorry_about_the__,but_for_some_reason_my_space_key_is_not_working.

---

### Post by JawsThemeSwimming428 on 2007-08-30
Thanks for the replies! I might give those a shot. I am debating whether or not just to run Ubuntu in a VM or to put the HDD in my Vista machine and dual boot. Any thoughts?

---

### Post by LaRoza on 2007-08-30
> **JawsThemeSwimming428 said:**
> Thanks for the replies! I might give those a shot. I am debating whether or not just to run Ubuntu in a VM or to put the HDD in my Vista machine and dual boot. Any thoughts?

If the Vista machine is better than the other, just put the hard drive in the new computer. You will probably want to just reinstall it, so back up all your data (copy you home folder, so you can easily transfer your settings).

I did this, it is much better. If you are using SATA drives, having Feisty on the first (0) SATA port is fine, and Vista will be on other.

-EDIT My KVM only has PS/2 for Mice, I thought this was a problem, until I bought a USB mouse that came with a PS/2 converter.

---

