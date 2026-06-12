---
title: "Problems using Sony Walkman device following upgrade to 9.10"
date: 2009-11-19
forum: Hardware
---

### Post by mashedbear on 2009-11-19
Hello,
I am having problems using Sony Walkman device following upgrade to 9.10. I am running 9.10 64bit & I use Banshee 1.6 Beta 2 (1.5.1). 

When I run mtp-detect I get the following:
> 
sudo mtp-detect 
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   Sony: Walkman NWZ-B135 (054c:036e) @ bus 0, dev 10
Attempting to connect device(s)
PTP_ERROR_IO: Trying again after re-initializing USB interface
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
Unable to open raw device 0
OK.

banshee log shows:

> PTP_ERROR_IO: Trying again after re-initializing USB interface
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
[Warn  10:36:53.858] Caught an exception - Connecting (in `Mtp')
  at Mtp.Error.CheckError (ErrorCode errorCode) [0x00000] 
  at Mtp.MtpDevice.GetConnectedDevices (System.IntPtr& list) [0x00000] 
  at Mtp.MtpDevice.Detect () [0x00000] 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000]

When the sony device is connected via usb banshee process sleeps - > futex_wait_queue_me - and process has to be killed. The Sony Walkman NWZ-B135 also has to be reset

I've seen that there are new releases of libtmp [http://libmtp.sourceforge.net/download.php]("http://libmtp.sourceforge.net/download.php"). Would upgrading to Release 1.0.1 solve this?

Any help appreciated.

Thanks

---

### Post by mashedbear on 2010-02-10
This problem is not solved. 

I have posted a bug report and banshee log to [banshee bugzilla]("https://bugzilla.gnome.org/show_bug.cgi?id=609593")

---

