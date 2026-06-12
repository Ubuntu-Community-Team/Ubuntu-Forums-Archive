---
title: "Late 2011 Macbook Pro 8,3 monitor wakeup from sleep and disable radeon"
date: 2019-09-06
forum: Hardware
---

### Post by ozialien on 2019-09-06
If you want to use you radeon driver for games etc....  I am not sure but I think switcheroo will do this if you install it despite perminent power off of radeon in this configuration.  I found that with radeon enabled on startup 18.04 wouldn't wakeup from suspend.  With intel it does.


/etc/defaults/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0 i915.lvds_channels=2 i915.modeset=1 i915.lvds_use_ssc=0 i915.i915_enable_rc6=1 elevator=noop amdgpu.runpm=0 acpi_backlight=intel_backlight"


/etc/grub.d/10_linux:

root@ernest-MacBookPro:/etc/grub.d# git diff HEAD~1 10_linux
diff --git a/grub.d/10_linux b/grub.d/10_linux
index 620980e..3f2a95d 100755
--- a/grub.d/10_linux
+++ b/grub.d/10_linux
@@ -136,6 +136,14 @@ linux_entry ()
   if [ "$quick_boot" = 1 ]; then
       echo "   recordfail" | sed "s/^/$submenu_indentation/"
   fi
+
+  if [ x$type != xrecovery ] ; then
+      echo "        outb 0x728 1" | sed "s/^/$submenu_indentation/"
+      echo "        outb 0x710 2" | sed "s/^/$submenu_indentation/"
+      echo "        outb 0x740 2" | sed "s/^/$submenu_indentation/"
+      echo "        outb 0x750 0" | sed "s/^/$submenu_indentation/"
+  fi 
+
   if [ x$type != xrecovery ] ; then
       save_default_entry | grub_add_tab
   fi
root@ernest-MacBookPro:/etc/grub.d#

---

