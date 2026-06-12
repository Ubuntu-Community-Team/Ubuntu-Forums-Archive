---
title: "Installing US Robotics 9000 in Ubuntu"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by Recall on 2006-02-26
I am a total noob with Linux and am just getting to grips with it. I cannot seem to get the drivers to compile for this modem. This is the error

> 
from /usr/include/linux/module.h:9,
                 from AdiUsbAdslDriver.c:32:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from AdiUsbAdslDriver.c:32:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
In file included from AdiUsbAdslDriver.c:34:
/usr/include/linux/proc_fs.h:245: error: field ‘vfs_inode’ has incomplete type
/usr/include/linux/proc_fs.h: In function ‘PROC_I’:
/usr/include/linux/proc_fs.h:250: error: syntax error before ‘struct’
AdiUsbAdslDriver.c:35:25: error: asm/uaccess.h: No such file or directory
AdiUsbAdslDriver.c: At top level:
AdiUsbAdslDriver.c:41: warning: ‘struct usb_device_id’ declared inside parameter list
AdiUsbAdslDriver.c:43: warning: ‘struct urb’ declared inside parameter list
AdiUsbAdslDriver.c:48: warning: ‘struct sk_buff’ declared inside parameter list
AdiUsbAdslDriver.c:53: error: syntax error before ‘*’ token
AdiUsbAdslDriver.c:53: warning: function declaration isn’t a prototype
AdiUsbAdslDriver.c:61: error: array type has incomplete element type
AdiUsbAdslDriver.c:62: warning: implicit declaration of function ‘USB_DEVICE’
AdiUsbAdslDriver.c:74: error: variable ‘adi_driver’ has initializer but incomplete type
AdiUsbAdslDriver.c:75: error: unknown field ‘name’ specified in initializer
AdiUsbAdslDriver.c:75: warning: excess elements in struct initializer
AdiUsbAdslDriver.c:75: warning: (near initialization for ‘adi_driver’)
AdiUsbAdslDriver.c:76: error: unknown field ‘id_table’ specified in initializer
AdiUsbAdslDriver.c:76: warning: excess elements in struct initializer
AdiUsbAdslDriver.c:76: warning: (near initialization for ‘adi_driver’)
AdiUsbAdslDriver.c:77: error: unknown field ‘probe’ specified in initializer
AdiUsbAdslDriver.c:77: warning: excess elements in struct initializer
AdiUsbAdslDriver.c:77: warning: (near initialization for ‘adi_driver’)
AdiUsbAdslDriver.c:78: error: unknown field ‘disconnect’ specified in initializer
AdiUsbAdslDriver.c:78: warning: excess elements in struct initializer
AdiUsbAdslDriver.c:78: warning: (near initialization for ‘adi_driver’)
AdiUsbAdslDriver.c:79: error: unknown field ‘ioctl’ specified in initializer
AdiUsbAdslDriver.c:79: warning: excess elements in struct initializer
AdiUsbAdslDriver.c:79: warning: (near initialization for ‘adi_driver’)
AdiUsbAdslDriver.c:83: error: syntax error before ‘modem’
AdiUsbAdslDriver.c:83: warning: type defaults to ‘int’ in declaration of ‘modem’AdiUsbAdslDriver.c:83: warning: data definition has no type or storage class
AdiUsbAdslDriver.c:91:41: error: missing binary operator before token "("
AdiUsbAdslDriver.c: In function ‘adi_init’:
AdiUsbAdslDriver.c:105: warning: implicit declaration of function ‘usb_register’AdiUsbAdslDriver.c:107: warning: implicit declaration of function ‘printk’
AdiUsbAdslDriver.c:107: error: ‘KERN_INFO’ undeclared (first use in this function)
AdiUsbAdslDriver.c:107: error: (Each undeclared identifier is reported only onceAdiUsbAdslDriver.c:107: error: for each function it appears in.)
AdiUsbAdslDriver.c:107: error: syntax error before string constant
AdiUsbAdslDriver.c: In function ‘adi_exit’:
AdiUsbAdslDriver.c:123: warning: implicit declaration of function ‘usb_deregister’
AdiUsbAdslDriver.c: At top level:
AdiUsbAdslDriver.c:140: error: conflicting types for ‘adi_probe’
AdiUsbAdslDriver.c:41: error: previous declaration of ‘adi_probe’ was here
AdiUsbAdslDriver.c: In function ‘adi_probe’:
AdiUsbAdslDriver.c:141: error: ‘u32’ undeclared (first use in this function)
AdiUsbAdslDriver.c:141: error: syntax error before ‘pid’
AdiUsbAdslDriver.c:151: error: ‘pid’ undeclared (first use in this function)
AdiUsbAdslDriver.c:151: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:153: warning: implicit declaration of function ‘usb_set_configuration’
AdiUsbAdslDriver.c:153: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:160: warning: implicit declaration of function ‘memset’
AdiUsbAdslDriver.c:160: warning: incompatible implicit declaration of built-in function ‘memset’
AdiUsbAdslDriver.c:162: error: request for member ‘usbdev’ in something not a structure or union
AdiUsbAdslDriver.c:193: error: request for member ‘IsoPipeSize’ in something not a structure or union
AdiUsbAdslDriver.c:194: error: request for member ‘IsoFramesPerUrb’ in something not a structure or union
AdiUsbAdslDriver.c:203: error: request for member ‘pipeBulkIdmaOut’ in something not a structure or union
AdiUsbAdslDriver.c:203: warning: implicit declaration of function ‘usb_sndbulkpipe’
AdiUsbAdslDriver.c:205: error: request for member ‘pipeBulkDataOut’ in something not a structure or union
AdiUsbAdslDriver.c:207: error: request for member ‘pipeBulkDataIn’ in something not a structure or union
AdiUsbAdslDriver.c:207: warning: implicit declaration of function ‘usb_rcvbulkpipe’
AdiUsbAdslDriver.c:209: error: request for member ‘pipeIsoDataIn’ in something not a structure or union
AdiUsbAdslDriver.c:209: warning: implicit declaration of function ‘usb_rcvisocpipe’
AdiUsbAdslDriver.c:211: error: request for member ‘pipeIntIn’ in something not a structure or union
AdiUsbAdslDriver.c:211: warning: implicit declaration of function ‘usb_rcvintpipe’
AdiUsbAdslDriver.c:214: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:214: warning: implicit declaration of function ‘kmalloc’
AdiUsbAdslDriver.c:214: warning: implicit declaration of function ‘in_interrupt’AdiUsbAdslDriver.c:214: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
AdiUsbAdslDriver.c:214: error: ‘GFP_KERNEL’ undeclared (first use in this function)
AdiUsbAdslDriver.c:215: error: request for member ‘pReadyData’ in something not a structure or union
AdiUsbAdslDriver.c:221: error: request for member ‘pUrbReadIso’ in something not a structure or union
AdiUsbAdslDriver.c:221: warning: implicit declaration of function ‘usb_alloc_urb’
AdiUsbAdslDriver.c:221: error: request for member ‘IsoFramesPerUrb’ in something not a structure or union
AdiUsbAdslDriver.c:222: error: request for member ‘pIncomingData’ in something not a structure or union
AdiUsbAdslDriver.c:222: error: request for member ‘IsoPipeSize’ in something not a structure or union
AdiUsbAdslDriver.c:222: error: request for member ‘IsoFramesPerUrb’ in something not a structure or union
AdiUsbAdslDriver.c:224: error: request for member ‘pIncomingData’ in something not a structure or union
AdiUsbAdslDriver.c:233: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:234: error: request for member ‘pReadyData’ in something not a structure or union
AdiUsbAdslDriver.c:247: error: request for member ‘ReassemblyBuffer’ in something not a structure or union
AdiUsbAdslDriver.c:248: error: request for member ‘ReassemblyBuffer’ in something not a structure or union
AdiUsbAdslDriver.c:248: error: request for member ‘pReadyData’ in something not a structure or union
AdiUsbAdslDriver.c:251: error: request for member ‘CtrlUrbFreeQ’ in something not a structure or union
AdiUsbAdslDriver.c:252: error: ‘USB_ST_NOERROR’ undeclared (first use in this function)
AdiUsbAdslDriver.c:258: warning: implicit declaration of function ‘INIT_LIST_HEAD’
AdiUsbAdslDriver.c:258: error: request for member ‘CtrlUrbPendQ’ in something not a structure or union
AdiUsbAdslDriver.c:266: warning: implicit declaration of function ‘init_timer’
AdiUsbAdslDriver.c:266: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:267: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:268: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:276: error: request for member ‘CtrlUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:277: error: request for member ‘CtrlUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:278: error: request for member ‘CtrlUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:284: error: request for member ‘ReadUrbFreeQ’ in something not a structure or union
AdiUsbAdslDriver.c:291: error: request for member ‘ReadUrbPendQ’ in something not a structure or union
AdiUsbAdslDriver.c:294: error: request for member ‘WriteUrbFreeQ’ in something not a structure or union
AdiUsbAdslDriver.c:301: error: request for member ‘WriteUrbPendQ’ in something not a structure or union
AdiUsbAdslDriver.c:304: error: request for member ‘ReadUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:305: error: request for member ‘ReadUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:306: error: request for member ‘ReadUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:307: warning: implicit declaration of function ‘mod_timer’
AdiUsbAdslDriver.c:307: error: request for member ‘ReadUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:307: error: ‘jiffies’ undeclared (first use in this function)AdiUsbAdslDriver.c:310: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:311: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:322: warning: implicit declaration of function ‘usb_driver_claim_interface’
AdiUsbAdslDriver.c:322: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:323: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:324: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:326: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:327: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:328: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:337: warning: implicit declaration of function ‘usb_set_interface’
AdiUsbAdslDriver.c:343: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:347: error: request for member ‘ptrlock’ in something not a structure or union
AdiUsbAdslDriver.c:347: error: ‘SPIN_LOCK_UNLOCKED’ undeclared (first use in this function)
AdiUsbAdslDriver.c:354: warning: implicit declaration of function ‘FILL_INT_URB’AdiUsbAdslDriver.c:354: error: request for member ‘urbInt’ in something not a structure or union
AdiUsbAdslDriver.c:354: error: request for member ‘pipeIntIn’ in something not a structure or union
AdiUsbAdslDriver.c:354: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:356: warning: implicit declaration of function ‘usb_submit_urb’
AdiUsbAdslDriver.c:356: error: request for member ‘urbInt’ in something not a structure or union
AdiUsbAdslDriver.c:360: warning: implicit declaration of function ‘init_etherdev’
AdiUsbAdslDriver.c:360: warning: assignment makes pointer from integer without a cast
AdiUsbAdslDriver.c:367: warning: implicit declaration of function ‘SET_MODULE_OWNER’
AdiUsbAdslDriver.c:373: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:376: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:384: warning: implicit declaration of function ‘strcpy’
AdiUsbAdslDriver.c:384: warning: incompatible implicit declaration of built-in function ‘strcpy’
AdiUsbAdslDriver.c:384: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:385: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:386: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:387: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:388: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:389: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:390: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:391: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:392: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:395: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:399: warning: implicit declaration of function ‘memcpy’
AdiUsbAdslDriver.c:399: warning: incompatible implicit declaration of built-in function ‘memcpy’
AdiUsbAdslDriver.c:399: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:399: error: request for member ‘MAC’ in something not a structure or union
AdiUsbAdslDriver.c:406: error: request for member ‘WriteStatus’ in something not a structure or union
AdiUsbAdslDriver.c:407: error: request for member ‘Writetime’ in something not a structure or union
AdiUsbAdslDriver.c:409: error: request for member ‘WriteUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:410: error: request for member ‘WriteUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:411: error: request for member ‘WriteUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:412: error: request for member ‘WriteUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c: In function ‘adi_disconnect’:
AdiUsbAdslDriver.c:440: error: invalid operands to binary *
AdiUsbAdslDriver.c:440: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:441: error: ‘u32’ undeclared (first use in this function)
AdiUsbAdslDriver.c:453: error: ‘pid’ undeclared (first use in this function)
AdiUsbAdslDriver.c:453: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:463: warning: implicit declaration of function ‘timer_pending’
AdiUsbAdslDriver.c:463: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:463: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:464: warning: implicit declaration of function ‘del_timer’
AdiUsbAdslDriver.c:464: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:464: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:465: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:465: error: request for member ‘CtrlUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:466: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:466: error: request for member ‘CtrlUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:467: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:467: error: request for member ‘ReadUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:468: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:468: error: request for member ‘ReadUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:469: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:469: error: request for member ‘WriteUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:470: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:470: error: request for member ‘WriteUrbQueueTimer’ in something not a structure or union
AdiUsbAdslDriver.c:473: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:473: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:475: warning: implicit declaration of function ‘unregister_netdev’
AdiUsbAdslDriver.c:475: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:475: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:476: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:476: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:480: warning: implicit declaration of function ‘usb_unlink_urb’
AdiUsbAdslDriver.c:480: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:480: error: request for member ‘urbInt’ in something not a structure or union
AdiUsbAdslDriver.c:483: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:483: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:483: warning: implicit declaration of function ‘kfree’
AdiUsbAdslDriver.c:483: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:483: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:483: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:483: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:485: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:485: error: request for member ‘pReadyData’ in something not a structure or union
AdiUsbAdslDriver.c:485: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:485: error: request for member ‘pReadyData’ in something not a structure or union
AdiUsbAdslDriver.c:485: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:485: error: request for member ‘pReadyData’ in something not a structure or union
AdiUsbAdslDriver.c:486: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:486: error: request for member ‘pDsp’ in something not a structure or union
AdiUsbAdslDriver.c:486: warning: implicit declaration of function ‘vfree’
AdiUsbAdslDriver.c:486: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:486: error: request for member ‘pDsp’ in something not a structure or union
AdiUsbAdslDriver.c:486: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:486: error: request for member ‘pDsp’ in something not a structure or union
AdiUsbAdslDriver.c:489: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:489: error: request for member ‘pIncomingData’ in something not a structure or union
AdiUsbAdslDriver.c:489: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:489: error: request for member ‘pIncomingData’ in something not a structure or union
AdiUsbAdslDriver.c:489: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:489: error: request for member ‘pIncomingData’ in something not a structure or union
AdiUsbAdslDriver.c:491: warning: implicit declaration of function ‘usb_free_urb’AdiUsbAdslDriver.c:491: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:491: error: request for member ‘pUrbReadIso’ in something not a structure or union
AdiUsbAdslDriver.c:501: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:501: error: request for member ‘CtrlUrbFreeQ’ in something not a structure or union
AdiUsbAdslDriver.c:502: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:502: error: request for member ‘CtrlUrbPendQ’ in something not a structure or union
AdiUsbAdslDriver.c:504: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:504: error: request for member ‘ReadUrbFreeQ’ in something not a structure or union
AdiUsbAdslDriver.c:505: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:505: error: request for member ‘ReadUrbPendQ’ in something not a structure or union
AdiUsbAdslDriver.c:507: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:507: error: request for member ‘WriteUrbFreeQ’ in something not a structure or union
AdiUsbAdslDriver.c:508: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:508: error: request for member ‘WriteUrbPendQ’ in something not a structure or union
AdiUsbAdslDriver.c:511: warning: implicit declaration of function ‘usb_driver_release_interface’
AdiUsbAdslDriver.c:511: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:512: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:513: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c: At top level:
AdiUsbAdslDriver.c:526: warning: ‘struct urb’ declared inside parameter list
AdiUsbAdslDriver.c:527: error: conflicting types for ‘adi_irq’
AdiUsbAdslDriver.c:43: error: previous declaration of ‘adi_irq’ was here
AdiUsbAdslDriver.c: In function ‘adi_irq’:
AdiUsbAdslDriver.c:528: error: invalid operands to binary *
AdiUsbAdslDriver.c:534: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:536: warning: implicit declaration of function ‘spin_lock_irqsave’
AdiUsbAdslDriver.c:536: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:536: error: request for member ‘ptrlock’ in something not a structure or union
AdiUsbAdslDriver.c:539: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:544: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:545: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:547: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:547: error: request for member ‘urbInt’ in something not a structure or union
AdiUsbAdslDriver.c:553: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:553: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:555: error: ‘pInt’ undeclared (first use in this function)
AdiUsbAdslDriver.c:557: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:557: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:557: error: request for member ‘pInterruptData’ in something not a structure or union
AdiUsbAdslDriver.c:562: error: ‘u16’ undeclared (first use in this function)
AdiUsbAdslDriver.c:562: error: syntax error before ‘SwapData’
AdiUsbAdslDriver.c:564: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:564: error: request for member ‘AdiModemSm’ in something not a structure or union
AdiUsbAdslDriver.c:565: error: ‘SwapData’ undeclared (first use in this function)
AdiUsbAdslDriver.c:582: warning: implicit declaration of function ‘spin_unlock_irqrestore’
AdiUsbAdslDriver.c:582: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:582: error: request for member ‘ptrlock’ in something not a structure or union
AdiUsbAdslDriver.c: In function ‘adi_open’:
AdiUsbAdslDriver.c:595: error: invalid operands to binary *
AdiUsbAdslDriver.c:595: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:608: warning: implicit declaration of function ‘netif_start_queue’
AdiUsbAdslDriver.c:611: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:611: error: request for member ‘IsOpen’ in something not a structure or union
AdiUsbAdslDriver.c: In function ‘adi_close’:
AdiUsbAdslDriver.c:622: error: invalid operands to binary *
AdiUsbAdslDriver.c:622: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:627: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:627: error: request for member ‘IsOpen’ in something not a structure or union
AdiUsbAdslDriver.c:630: warning: implicit declaration of function ‘netif_stop_queue’
AdiUsbAdslDriver.c: In function ‘adi_stats’:
AdiUsbAdslDriver.c:661: error: invalid operands to binary *
AdiUsbAdslDriver.c:661: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:666: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:666: error: request for member ‘LinuxStats’ in something not a structure or union
AdiUsbAdslDriver.c: At top level:
AdiUsbAdslDriver.c:672: warning: ‘struct sk_buff’ declared inside parameter listAdiUsbAdslDriver.c:673: error: conflicting types for ‘adi_start_xmit’
AdiUsbAdslDriver.c:48: error: previous declaration of ‘adi_start_xmit’ was here
AdiUsbAdslDriver.c: In function ‘adi_start_xmit’:
AdiUsbAdslDriver.c:674: error: invalid operands to binary *
AdiUsbAdslDriver.c:674: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:694: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:694: error: request for member ‘MpoaMode’ in something not a structure or union
AdiUsbAdslDriver.c:698: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:698: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:703: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:703: warning: implicit declaration of function ‘__constant_htons’
AdiUsbAdslDriver.c:705: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:705: error: dereferencing pointer to incomplete type
In file included from AdiUsbAdslDriver.c:1022:
/usr/include/linux/if_arp.h:150:1: error: unterminated argument list invoking macro "ZAP"
AdiUsbAdslDriver.c:1023: error: ‘ZAP’ undeclared (first use in this function)
AdiUsbAdslDriver.c:1023: error: syntax error before ‘struct’
AdiUsbAdslDriver.c:1041: warning: unused variable ‘ar_tip’
AdiUsbAdslDriver.c:1040: warning: unused variable ‘ar_tha’
AdiUsbAdslDriver.c:1039: warning: unused variable ‘ar_sip’
AdiUsbAdslDriver.c:1038: warning: unused variable ‘ar_sha’
AdiUsbAdslDriver.c:1032: warning: unused variable ‘ar_op’
AdiUsbAdslDriver.c:1031: warning: unused variable ‘ar_pln’
AdiUsbAdslDriver.c:1030: warning: unused variable ‘ar_hln’
AdiUsbAdslDriver.c:1029: warning: unused variable ‘ar_pro’
AdiUsbAdslDriver.c:1028: warning: unused variable ‘ar_hrd’
AdiUsbAdslDriver.c:1027: warning: unused variable ‘h_proto’
AdiUsbAdslDriver.c:1026: warning: unused variable ‘h_source’
AdiUsbAdslDriver.c:1046: error: syntax error before ‘*’ token
AdiUsbAdslDriver.c:1047: error: invalid storage class for function ‘LocalArpReply’
AdiUsbAdslDriver.c:1047: warning: function declaration isn’t a prototype
AdiUsbAdslDriver.c: In function ‘LocalArpReply’:
AdiUsbAdslDriver.c:1048: error: ‘pPacket’ undeclared (first use in this function)
AdiUsbAdslDriver.c:1049: error: storage size of ‘ReplyArpPkt’ isn’t known
AdiUsbAdslDriver.c:1053: error: invalid application of ‘sizeof’ to incomplete type ‘struct EthArpPkt’
AdiUsbAdslDriver.c:1056: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1060: warning: incompatible implicit declaration of built-in function ‘memcpy’
AdiUsbAdslDriver.c:1065: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1066: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1069: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1072: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1074: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1079: warning: implicit declaration of function ‘dev_alloc_skb’
AdiUsbAdslDriver.c:1079: warning: assignment makes pointer from integer without a cast
AdiUsbAdslDriver.c:1084: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1084: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:1084: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:1086: warning: implicit declaration of function ‘eth_copy_and_sum’
AdiUsbAdslDriver.c:1086: error: ‘u8’ undeclared (first use in this function)
AdiUsbAdslDriver.c:1086: error: syntax error before ‘)’ token
AdiUsbAdslDriver.c:1087: warning: implicit declaration of function ‘skb_put’
AdiUsbAdslDriver.c:1088: error: dereferencing pointer to incomplete type
AdiUsbAdslDriver.c:1088: warning: implicit declaration of function ‘eth_type_trans’
AdiUsbAdslDriver.c:1088: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:1088: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:1089: warning: implicit declaration of function ‘netif_rx’
AdiUsbAdslDriver.c:1091: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:1091: error: request for member ‘pLinuxNet’ in something not a structure or union
AdiUsbAdslDriver.c:1091: error: ‘jiffies’ undeclared (first use in this function)
AdiUsbAdslDriver.c:1092: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:1092: error: request for member ‘LinuxStats’ in something not a structure or union
AdiUsbAdslDriver.c:1093: warning: dereferencing ‘void *’ pointer
AdiUsbAdslDriver.c:1093: error: request for member ‘LinuxStats’ in something not a structure or union
AdiUsbAdslDriver.c:1049: warning: unused variable ‘ReplyArpPkt’
AdiUsbAdslDriver.c: In function ‘adi_start_xmit’:
AdiUsbAdslDriver.c:1096: error: syntax error at end of input
make: *** [AdiUsbAdslDriver.o] Error 1


I got them from here [http://www.usrobotics.com/support/product-template.asp?prod=9000](http://www.usrobotics.com/support/product-template.asp?prod=9000) following the guide did not help totally. Only way I could get it to attempt to compile is to use the command ./inst_mod linux then I get the above error.

Help is much appreciated.

---

