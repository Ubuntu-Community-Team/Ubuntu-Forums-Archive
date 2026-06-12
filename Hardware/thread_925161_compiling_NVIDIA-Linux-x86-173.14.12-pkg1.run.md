---
title: "compiling NVIDIA-Linux-x86-173.14.12-pkg1.run"
date: 2008-09-20
forum: Hardware
---

### Post by dfacto on 2008-09-20
Upgrading to 2.6.27-3-generic #1 SMP Mon Sep 15 14:08:09 UTC 2008 i686 GNU/Linux seemed to have broken nvidia-glx which I was using for:
```

$ lspci | grep VGA
nVidia Corporation NV44A [GeForce 6200] (rev a1)
```

None of the nvidia packages worked (including envyng) so I grabbed  NVIDIA-Linux-x86-173.14.12-pkg1.run from nvidia.com.

This would choke on compile, so I made the following changes (sorry I'm not making a patch file nor am I going to explain this in detail):

```

$ grep -nHi --color "smp_call_function" *
nv.c:1299:                //smp_call_function(__nv_setup_pat_entries, hcpu, 1, 1);
nv.c:1300:                smp_call_function(__nv_setup_pat_entries, hcpu, 1);
nv.c:1307:                //smp_call_function(__nv_restore_pat_entries, hcpu, 1, 1);
nv.c:1308:                smp_call_function(__nv_restore_pat_entries, hcpu, 1);
nv-linux.h:668:    //ret = smp_call_function(func, info, 1, 1);
nv-linux.h:669:    ret = smp_call_function(func, info, 1);
os-interface.c:51:    //ret = smp_call_function(ipi_handler, NULL, 1, 0);
os-interface.c:52:    ret = smp_call_function(ipi_handler, NULL, 1);

$ grep -nHi --color "semaphore.h" *
nv-linux.h:107://#include <asm/semaphore.h>
nv-linux.h:108:#include <linux/semaphore.h>

# [http://www.nvnews.net/vbulletin/showthread.php?t=116827](http://www.nvnews.net/vbulletin/showthread.php?t=116827)
$ grep -EnHi --color "kill_p.*(pid, sig, 1)" *
os-interface.c:707:    //return kill_proc(pid, sig, 1) ? RM_ERR_OPERATING_SYSTEM : RM_OK;
os-interface.c:708:    return kill_pid(pid, sig, 1) ? RM_ERR_OPERATING_SYSTEM : RM_OK;
```

Basically the above is the commented line and the fixed line.  Notice that I simply dropped the last arg to all instances of smp_call_function, changed asm/semaphore.h to linux/semaphore.h and used kill_pid instead of kill_proc (this last one could apparently be commented out altogther, meh).  Be advised, NVIDIA-Linux-x86-173.14.12-pkg1.run extracts to /tmp from which you can copy to ~ edit the three files and rerun nvidia-installer.

Everything is working now.

PS you may want to ```
sudo aptitude --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings nvidia-glx-new-dev-envy  nvidia-glx-new-envy  nvidia-new-kernel-source-envy
``` before doing above.  You will also need to stop X ```
sudo invoke-rc.d gdm stop
``` if youre in gnome.

---

