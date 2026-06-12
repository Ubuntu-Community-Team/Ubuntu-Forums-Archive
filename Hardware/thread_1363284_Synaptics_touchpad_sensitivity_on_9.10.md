---
title: "Synaptics touchpad sensitivity on 9.10"
date: 2009-12-24
forum: Hardware
---

### Post by Giovano on 2009-12-24
Hey guys,

I had some trouble trying to adjust the sensitivity of the touchpad on Ubuntu 9.10

gpointing-device-settings does not offer this feature, and gsynaptics did not have any effect. 

I enabled SHMconfig by creating a new file named **/etc/hal/fdi/policy/shmconfig.fdi** with these contents:
> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>[FONT=Verdana]
[/FONT]And restarting the system.

But event after that, gsynaptic uses synclient which produces this error (in the console) when adjusting sensitivity:

> X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0xf3
  Serial number of failed request:  20
  Current serial number in output stream:  21
The solution I found is to use synclient directly, with the -s option.
For instance:
> 
synclient -s FingerLow=35 FingerHigh=40
And this works. To make this change permanent I added this command in a new file named /etc/X11/Xsession.d/91-synclient

Hope this helps.

---

### Post by PrimaryMaster on 2010-03-02
Hi,

I followed the same path you did. Enabled SHMConfig and installed gsynaptics. Using the GUI leads to the same error. I fiddled with synclient for a while. 

The setting you provided (FingerLow=35) is "OUT OF LIMITS", warns synclient. The max allowed for FingerLow is "30".

So I set mine to low 30, high 40. I wonder what that does. I don't feel a change. 

Regards,
PM

---

### Post by MooseMagnet on 2010-12-01
I just switched from 8 to 9.1. Same problem with the touchpad. Thanks for your post.

Synclient -l says FingerLow=10 and FingerHigh=15

I changed them to 35 and 40 respectively. This improved my touchpad performance greatly. But when I repeat Synclient -l it still lists Low=10 and High=15.

Seems strange. 

Do you know which settings regulate the cursor speed?

thanks.
R-

---

