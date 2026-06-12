---
title: "CUPS cannot differentiate between two DYMO printers installed on USB"
date: 2020-04-19
forum: Hardware
---

### Post by pldaniels on 2020-04-19
With a single DYMO LabelWriter 450 printer on my system (Ubuntu 20.04 on iMac 27" 2013) everything is fine.

I've installed a second DYMO printer of the same model, and while both are uniquely detected and allocated a separate /dev/lp* port, CUPS however cannot see the two.

The problem it appears is that CUPS generates a DeviceURI based on the IEEE1284 string from the USB  

> ATTRS{ieee1284_id}=="MFG:DYMO;CMD: ;MDL:LabelWriter 450;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450|SERN:010113251519" 

...which unfortunately is *not* unique between printers, because that "SERN:" portion is more of a printer-model SERN, where's the *true* serial number is ATTRS{serial}=="19061300590791" from  udevadm info --attribute-walk --name=/dev/usb/lpX

I have added a udev ruleset to assign unique lp ports for each as well but to no avail ( the ports are correctly generated but CUPS again doesn't seem to see them as devices )

I even went as far as compiling a modified usblp kernel module that'd use the ATTRS{serial} data in the ieee1284 ID string, but still no avail (I suspect it's a RO property anyhow) even though it'll show up in the udevadm attribute walk.

So, I guess my question is more of a CUPS one,  how does one explicitly specify the different ports to use in the DeviceURI parameter in CUPS?  I've tried modifying the ppd's with the /dev/lp* explicitly defined to no avail.

Regards,
Paul.

---

### Post by pldaniels on 2020-04-20
Turns out that there's a bug in the CUPS usb-libusb.c code preventing the proper reading of the serial numbers from USB devices (amazed it's not been picked up in all these years).

```
  /*
1270   * Get the make, model, and serial numbers...
1271   */
1272 
1273   num_values = _cupsGet1284Values(device_id, &values);
1274 
1275   if ((sern = cupsGetOption("SERIALNUMBER", num_values, values)) == NULL)
1276     if ((sern = cupsGetOption("SERN", num_values, values)) == NULL)
1277       if ((sern = cupsGetOption("SN", num_values, values)) == NULL &&
1278      ((libusb_get_device_descriptor(printer->device, &devdesc) >= 0) &&
1279       devdesc.iSerialNumber))
1280       {
1281        /*
1282         * Try getting the serial number from the device itself...
1283    */
1284 
1285         int length =
1286      libusb_get_string_descriptor_ascii(printer->handle,
1287                     devdesc.iSerialNumber,
1288                     (unsigned char *)tempsern,
1289                     sizeof(tempsern) - 1);
1290         if (length > 0)
1291    {
1292      tempsern[length] = '\0';
1293      sern             = tempsern;
1294    }
1295       }

```

is missing an essential > libusb_get_device_descriptor( printer->device, &devdesc ); // load the data in to the descriptor
 line before trying to access the serial number data.

Overall though I've now rewritten the code so that it checks first for the USB serial number presence before trying to extract it from the IEEE1284 string.

As a result, the usb backend now correctly shows the DYMO serial numbers and cups shows two separate devices.


```
DEBUG2: Printer found with device ID: MFG:DYMO;CMD: ;MDL:LabelWriter 450;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450;SERN:01010112345600; Device URI: usb://DYMO/LabelWriter%20450?serial=19061300590791
direct usb://DYMO/LabelWriter%20450?serial=19061300590791 "DYMO LabelWriter 450" "DYMO LabelWriter 450" "MFG:DYMO;CMD: ;MDL:LabelWriter 450;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450;SERN:01010112345600;" ""
DEBUG2: Printer found with device ID: MFG:DYMO;CMD: ;MDL:LabelWriter 450;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450;SERN:01010112345600; Device URI: usb://DYMO/LabelWriter%20450?serial=19091715321065
direct usb://DYMO/LabelWriter%20450?serial=19091715321065 "DYMO LabelWriter 450" "DYMO LabelWriter 450" "MFG:DYMO;CMD: ;MDL:LabelWriter 450;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450;SERN:01010112345600;" ""
```


Code after changes / modifications for the make_device_uri() function ...

```

/*
 * 'make_device_uri()' - Create a device URI for a USB printer.
 */

static char *				/* O - Device URI */
make_device_uri(
    usb_printer_t *printer,		/* I - Printer */
    const char    *device_id,		/* I - IEEE-1284 device ID */
    char          *uri,			/* I - Device URI buffer */
    size_t        uri_size)		/* I - Size of device URI buffer */
{
  struct libusb_device_descriptor devdesc; /* Holds USB device information after loaded */
                                        /* Current device descriptor */
  char		options[1024];		/* Device URI options */
  int		num_values;		/* Number of 1284 parameters */
  cups_option_t	*values;		/* 1284 parameters */
  const char	*mfg,			/* Manufacturer */
		*mdl,			/* Model */
		*des = NULL,		/* Description */
		*sern = NULL;			/* Serial number */
  size_t	mfglen;			/* Length of manufacturer string */
  int sernlen; /* serial number length */
  char		tempmfg[256],		/* Temporary manufacturer string */
		tempsern[256],		/* Temporary serial number string */
		*tempptr;		/* Pointer into temp string */



 /*
  * Get the make, model, and serial numbers...
  */

	/*
	 * Attempt to get the serial number from the USB device first
	 * as sometimes the ieee1284 does not have a unique code (DYMO!)
	 */
	libusb_get_device_descriptor( printer->device, &devdesc ); // load the data in to the descriptor
	sernlen = libusb_get_string_descriptor_ascii( printer->handle
			, devdesc.iSerialNumber
			, (unsigned char *)tempsern
			, sizeof(tempsern) -1 );
	
	if (sernlen > 0) {
		tempsern[sernlen] = '\0';
		sern = tempsern;
	}

	/*
	 * Get the IEEE1284 data
	 */
  num_values = _cupsGet1284Values(device_id, &values);

  if (sern == NULL) {
	  if ((sern = cupsGetOption("SERIALNUMBER", num_values, values)) == NULL) {
		 if ((sern = cupsGetOption("SERN", num_values, values)) == NULL) {
			if ((sern = cupsGetOption("SN", num_values, values)) == NULL) {
				tempsern[0] = '\0';
				sern = tempsern;
			}
		 }
	  }
	} // sern == NULL

```


I'll see if I can submit this fix to the cups repo.

---

