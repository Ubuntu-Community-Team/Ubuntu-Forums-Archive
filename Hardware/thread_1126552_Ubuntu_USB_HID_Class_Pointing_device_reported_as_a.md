---
title: "Ubuntu USB: HID Class Pointing device reported as absolute mouse, treated as relative"
date: 2009-04-15
forum: Hardware
---

### Post by samclark on 2009-04-15
I'm developing a touch pad for ubuntu 8.04 and I'm having problems using it as a mouse. The mouse descriptors are as follows:

	0x05, 0x01, 					// USAGE_PAGE (Generic Desktop)
	0x09, 0x02, 					// USAGE (Mouse)
	0xa1, 0x01, 					// COLLECTION (Application)
	0x85, 0x01, 					//   REPORT ID 1
	0x09, 0x01, 					//	 USAGE (Pointer)
	0xa1, 0x00, 					//	 COLLECTION (Physical)
	0x05, 0x09, 					//	   USAGE_PAGE (Button)
	0x19, 0x01, 					//	   USAGE_MINIMUM (Button 1)
	0x29, 0x03, 					//	   USAGE_MAXIMUM (Button 3)
	0x15, 0x00, 					//	   LOGICAL_MINIMUM (0)
	0x25, 0x01, 					//	   LOGICAL_MAXIMUM (1)
	0x95, 0x03, 					//	   REPORT_COUNT (3)
	0x75, 0x01, 					//	   REPORT_SIZE (1)
	0x81, 0x02, 					//	   INPUT (Data,Var,Abs)
	0x95, 0x01, 					//	   REPORT_COUNT (1)
	0x75, 0x05, 					//	   REPORT_SIZE (5)
	0x81, 0x01, 					//	   INPUT (Cnst,Var,Abs)
	0x05, 0x01, 					//	   USAGE_PAGE (Generic Desktop)
	0x09, 0x30, 					//	   USAGE (X)
	0x09, 0x31, 					//	   USAGE (Y)
	0x15, 0x00, 					//	   LOGICAL_MINIMUM (0)
	0x26, 0xff, 0x07,				//	   LOGICAL_MAXIMUM (2047)
	0x35, 0x00, 					//	   PHYSICAL_MINIMUM (0)
	0x46, 0xff, 0x07,				//	   PHYSICAL_MAXIMUM (2047)
	0x75, 0x0c, 					//	   REPORT_SIZE (12)
	0x95, 0x02, 					//	   REPORT_COUNT (2)
	0x81, 0x02, 					//	   INPUT (Data,Var,Abs)
	0xc0,							//	 END_COLLECTION
	0xc0,							// END_COLLECTION

As you can see this is a very common (you could go as far to say this is THE HID mouse descriptor implementation) mouse implementation you could probably find exact copies of all over the web. You can see that the XY inputs are reported as absolute values (0x81, 0x01).

The problem is that the device XYs seem to be treated 'relatively'. For example if you touch (click) and drag from a known point and then touch the same point, the XY will be reported in a different place than the starting point of the drag. I can confirm that the device is not faulty as my absolute point reporting works using proprietary drivers. You wouldn't really be able to tell the difference between relative and absolute mouse with an ordinary mouse for obvious reasons, you can only tell using a touch device. Am I basically SOL or is there something I can do about this?

And a side question: 

in the output from > lsusb -v -d XXXX:YYYY

Will I ever be able to see the report descriptors or are they always hidden? (Report Descriptors: ** UNAVAILABLE **) Or is ** UNAVAILABLE ** bad?

---

