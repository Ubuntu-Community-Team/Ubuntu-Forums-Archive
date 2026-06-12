---
title: "PCI-Express Device Error, freeze on shutdown"
date: 2008-10-31
forum: General Help
---

### Post by leifjonny on 2008-10-31
After upgrade to Intrepid the computer freezes when i try to shut it down. Also boot up takes a long time (apart from the disk checks too). I have no idea what causes this. I have tried using both NVIDIA drivers provided by the installation (version 173 and version 177).
All help is appreciated.

dmesg is full of this:

[ 4223.986611] +------ PCI-Express Device Error ------+
[ 4223.986613] Error Severity		: Uncorrected (Non-Fatal)
[ 4223.986615] PCIE Bus Error type	: Transaction Layer
[ 4223.986628] Flow Control Protocol 	: First
[ 4223.986629] Receiver ID		: 0010
[ 4223.986631] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
[ 4223.986633] pcieport-driver 0000:00:02.0: broadcast error_detected message
[ 4223.986636] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
[ 4223.986638] pcieport-driver 0000:00:02.0: broadcast resume message
[ 4223.986662] pcieport-driver 0000:00:02.0: AER driver successfully recovered

---

