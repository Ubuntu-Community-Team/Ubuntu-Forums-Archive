---
title: "Driver compilation for elo touch screen fails on 13.10"
date: 2014-03-16
forum: Hardware
---

### Post by alexandermartin79 on 2014-03-16
A touch screen driver compilation fails on Ubuntu 13.10, but runs successfully on 13.04. The two errors on 13.10 are **implicit declaration of function** warnings treated as errors. Did the compiler standard flags change with 13.10? Did I miss something else? Any other suggestions on fixing the compilation?

**Edit1:** Annotation: The directory */lib/modules/$(shell uname -r)/build* used in Makefile seems to have moved to */usr/src/linux-headers-3.11.0-18-generic* in standard 13.10. After changing Makefile respectively still no success when compiling.

The build-essentials package is installed. A simple ```
make -k
``` or ```
make -i
``` command won't yield the o-file.

The compilation error is:

```
user1@pc:/etc/opt/elo-mt-usb/elo_mt_input_mod_src$ sudo make
make -C /lib/modules/3.11.0-18-generic/build SUBDIRS=/etc/opt/elo-mt-usb/elo_mt_input_mod_src modules 
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.11.0-18-generic'
  CC [M]  /etc/opt/elo-mt-usb/elo_mt_input_mod_src/elo_mt_input.o
/etc/opt/elo-mt-usb/elo_mt_input_mod_src/elo_mt_input.c: In function &#8216;elo_input_write&#8217;:
/etc/opt/elo-mt-usb/elo_mt_input_mod_src/elo_mt_input.c:79:2: error: implicit declaration of function &#8216;kzalloc&#8217; [-Werror=implicit-function-declaration]
  if(!(buffer = kzalloc(count, GFP_KERNEL))) 
  ^
/etc/opt/elo-mt-usb/elo_mt_input_mod_src/elo_mt_input.c:79:14: warning: assignment makes pointer from integer without a cast [enabled by default]
  if(!(buffer = kzalloc(count, GFP_KERNEL))) 
              ^
/etc/opt/elo-mt-usb/elo_mt_input_mod_src/elo_mt_input.c:148:3: error: implicit declaration of function &#8216;kfree&#8217; [-Werror=implicit-function-declaration]
   kfree(buffer);
   ^
cc1: some warnings being treated as errors
make[2]: *** [/etc/opt/elo-mt-usb/elo_mt_input_mod_src/elo_mt_input.o] Fehler 1
make[1]: *** [_module_/etc/opt/elo-mt-usb/elo_mt_input_mod_src] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.11.0-18-generic'
make: *** [default] Fehler 2

```
Luckily, the manufacturer published the driver source under the GPL. The elo_mt_input.c file is:
```

// --------------------------------------------------------------
// Name:    Linux input module for Elo MultiTouch(MT) devices
// License: GPL
// Author:  Elo Touch Solutions Inc
// Version: 1.0.0 
// Date:    26 August 2013
// --------------------------------------------------------------

//Header Files
#include <linux/module.h>
#include <linux/proc_fs.h>
#include <asm/uaccess.h>
#include <linux/version.h>
#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,38))
 #include <linux/input/mt.h>
#else
 #include <linux/input.h>
#endif

//Driver Information
#define DRIVER_VERSION  "1.0.0"
#define DRIVER_AUTHOR   "Elo Touch Solutions Inc"
#define DRIVER_DESC     "Linux input module for Elo MultiTouch(MT) devices"
#define DRIVER_LICENSE  "GPL"

// Kernel Module Information
MODULE_VERSION(DRIVER_VERSION);
MODULE_AUTHOR(DRIVER_AUTHOR);
MODULE_DESCRIPTION(DRIVER_DESC);
MODULE_LICENSE(DRIVER_LICENSE);

// Global Definitions
#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,38))
 #define _MULTITOUCH_KERNEL_
#else
 #undef _MULTITOUCH_KERNEL_
#endif

#ifdef _MULTITOUCH_KERNEL_
 #define ELO_MT_MAXCONTACTS 2  // Maximum number of multi touch contacts
#endif

#define MIN_X (0)    // Min X Axis resolution
#define MAX_X (4095) // Max X Axis resolution 

#define MIN_Y (0)    // Min Y Axis resolution 
#define MAX_Y (4095) // Max Y Axis resolution

#define MIN_PRESSURE (0) // Min Pressure 
#define MAX_PRESSURE (1) // Max Pressure

// Global Data Structures
struct touch_event {
 u16 touch_count;   // Total touch count in the entire frame
 u16 touch_index;   // Current Touch Index for this contact
 u16 contact_id;    // Contact ID for this contact
 u16 touch_status;  // Indicates if touch is active or not for this contact
 u16 x;             // ABS X value for this contact
 u16 y;             // ABS Y value for this contact
};

struct input_dev *elo_input_device = NULL;
struct proc_dir_entry *proc_entry = NULL;

// Functions
static ssize_t elo_input_read(struct file *file, char __user *buf, size_t count, loff_t *ppos)
{
 return 0;
}

static ssize_t elo_input_write(struct file *file, const char __user *buf, size_t count, loff_t *ppos)
{
 int rc = -1;
 const u8 *ptr = NULL;
 u8 *buffer = NULL;
 size_t size = count;
 struct touch_event *event = NULL;

 if(!(buffer = kzalloc(count, GFP_KERNEL))) 
  {
   printk(KERN_ERR "elo_mt_input: Unable to allocate memory\n");
   rc = -ENOMEM;
   goto done;
  }

 if(copy_from_user(buffer, buf, count)) 
  {
   printk(KERN_ERR "elo_mt_input: Unable to copy data\n");
   rc = -EFAULT;
   goto done;
  }

 /* Process each touch event */
 ptr = buffer;

 while(size >= sizeof(*event)) 
  {
   event = (struct touch_event *)ptr;
   // printk(KERN_INFO "elo_mt_input: mt event touch#:%d cid=%d x=%d y=%d status=%d\n", event->touch_index, event->contact_id, event->x, event->y, event->touch_status);

#ifdef _MULTITOUCH_KERNEL_
   // Actions for sending Multitouch events  
   input_mt_slot(elo_input_device, event->contact_id); //Use contact_id for slot numbering [ max 2 slots ]
   input_mt_report_slot_state(elo_input_device, MT_TOOL_FINGER, event->touch_status);

   if(event->touch_status)
    {// If touch is active                  
     input_event(elo_input_device, EV_ABS, ABS_MT_POSITION_X, event->x);
     input_event(elo_input_device, EV_ABS, ABS_MT_POSITION_Y, event->y);
     input_event(elo_input_device, EV_ABS, ABS_MT_PRESSURE, event->touch_status);
    }
   // Send primary touch events to move the pointer
   input_mt_report_pointer_emulation(elo_input_device, true);

   // Check if this is the last touch event based on touch count and touch id, then send SYN_REPORT 
   if(event->touch_count == (event->touch_index + 1)) 
    {
     input_sync(elo_input_device);
    }
#else
   // Actions for sending Single Touch as Mouse events for primary touch only 
   if(event->touch_index == 0)
    {
     if(event->touch_status)
      {// If touch is active                  
       input_event(elo_input_device, EV_ABS, ABS_X, event->x);
       input_event(elo_input_device, EV_ABS, ABS_Y, event->y);
       input_event(elo_input_device, EV_KEY, BTN_LEFT, event->touch_status);
      }
     else
      {
       input_event(elo_input_device, EV_ABS, ABS_X, event->x);
       input_event(elo_input_device, EV_ABS, ABS_Y, event->y);
       input_event(elo_input_device, EV_KEY, BTN_LEFT, 0);
      }
     input_sync(elo_input_device);
    }
#endif

   ptr += sizeof(*event);       
   size -= sizeof(*event);
  }

 rc = count;

done:
 if(buffer)
  kfree(buffer);

 *ppos += count;
 return rc;
}

static const struct file_operations elo_input_fops = {
 .read  = elo_input_read,
 .write = elo_input_write
};

static int __init elo_input_init(void)
{
 int rc = 0;

 if(!(elo_input_device = input_allocate_device())) 
  {
   printk(KERN_ERR "elo_mt_input: Unable to create input_dev\n");
   rc = -EBUSY;
   goto done;
  }

 // Input device will report ABS events
 set_bit(EV_ABS, elo_input_device->evbit);

#ifdef _MULTITOUCH_KERNEL_
 // Setup for direct devices [touchscreens]
 set_bit(INPUT_PROP_DIRECT, elo_input_device->propbit);
 // Corresponding to HID TIPSWITCH field (Pointer emulation)
 input_set_capability(elo_input_device, EV_KEY, BTN_TOUCH);
 elo_input_device->name = "Elo MultiTouch(MT) Device Input Module";
#else
 // Corresponding to HID TIPSWITCH field - Send LEFT Mouse button event
 input_set_capability(elo_input_device, EV_KEY, BTN_LEFT);
 elo_input_device->name = "Elo Single Touch Device Input Module";
#endif


 // Set appropriate dimensions
 input_set_abs_params(elo_input_device, ABS_X,         MIN_X, MAX_X, 0, 0);
 input_set_abs_params(elo_input_device, ABS_Y,         MIN_Y, MAX_Y, 0, 0);

#ifdef _MULTITOUCH_KERNEL_
 input_set_abs_params(elo_input_device, ABS_MT_POSITION_X, MIN_X, MAX_X, 0, 0);
 input_set_abs_params(elo_input_device, ABS_MT_POSITION_Y, MIN_Y, MAX_Y, 0, 0);
 input_set_abs_params(elo_input_device, ABS_MT_PRESSURE,   MIN_PRESSURE, MAX_PRESSURE, 0, 0);
 input_set_abs_params(elo_input_device, ABS_PRESSURE,      MIN_PRESSURE, MAX_PRESSURE, 0, 0);

 // Corresponding to HID contact ID
 #if (LINUX_VERSION_CODE >= KERNEL_VERSION(3,7,0))
  input_mt_init_slots(elo_input_device, ELO_MT_MAXCONTACTS, INPUT_MT_DIRECT);  // Kernel 3.7 or later [Added 3rd parameter - flags] 
 #else
  input_mt_init_slots(elo_input_device, ELO_MT_MAXCONTACTS); 
 #endif 
#endif 

 if((rc = input_register_device(elo_input_device))) 
  {
   printk(KERN_ERR "elo_mt_input: Unable to register input_dev\n");
   goto done;
  }

 // Create the proc entry
 proc_entry = proc_create("elo_mt_input", S_IWUSR | S_IRUSR, NULL, &elo_input_fops);

 if(proc_entry == NULL) 
  {
   printk(KERN_ERR "elo_mt_input: Failed to create /proc/elo_mt_input\n");
   input_unregister_device(elo_input_device);
   rc = -EBUSY;
   goto done;
  } 

 printk(KERN_INFO "elo_mt_input: Input device registered\n");

done:
 return rc;
}

static void __exit elo_input_exit(void)
{
 remove_proc_entry("elo_mt_input", NULL);
 input_unregister_device(elo_input_device);
}

module_init(elo_input_init);
module_exit(elo_input_exit);


//---------------------------------EOF---------------------------------
```

The make file contains:

```
obj-m := elo_mt_input_mod.o 
elo_mt_input_mod-objs := elo_mt_input.o

KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules 

install:
    cp ./elo_mt_input_mod.ko ../elo_mt_input_mod_`uname -r`.ko

clean:
    rm -f *.o *.cmd *.mod.c .*.o* .*.ko* *~ *.ko Module.markers modules.order Module.symvers 
    rm -rf .tmp_versions/

```

---

### Post by Yellow Pasque on 2014-03-16
If you add this line to the #includes, does it help:
```
#include <linux/slab.h>
```

---

### Post by alexandermartin79 on 2014-03-17
Yes, works. Thank you.

---

