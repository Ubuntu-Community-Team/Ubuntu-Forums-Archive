---
title: "Transparent background with Firefox addon panels"
date: 2012-08-08
forum: Hardware
---

### Post by hickhack on 2012-08-08
Hello,

I have a new computer with Windows 7 and Ubuntu 12.04 installed. 

_My problem is as follow:_

Firefox Addon panels do not have a background at Ubuntu. The same Addon panel is correctly displayed at Windows 7.

The panel is created by a Firefox Addon. The Addon is: [https://addons.mozilla.org/de/firefox/addon/web-search-optimizer](https://addons.mozilla.org/de/firefox/addon/web-search-optimizer)

_My configuration:_

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

AMD RADEON HD 6450
Beschreibung: VGA compatible controller
Produkt: Caicos [Radeon HD 6450]
Hersteller: Hynix Semiconductor (Hyundai Electronics)
Physische ID: 0
Bus-Informationen: pci@0000:01:00.0
Version: 00
Breite: 64 bits
Uhr: 33MHz
Fähigkeiten: pm pciexpress msi vga_controller bus_master cap_list rom
Konfiguration: driver=fglrx_pci latency=0

Firefox: 14.01

I attached two screenshots. The Windows screenshot displays the panel with the correct background. The Ubuntu screenshot shows the missing background of the panel.
I added the xorg.conf, too.

I installed the fglrx driver via "System preferences" -> "Proprietary driver"

I would be thankful for some ideas.

Best regards,
Andre

---

### Post by hickhack on 2012-08-08
I made some progress and it seems that error is in the firefox addon panel object.

I have the following definiton in my lib/main.js file:

```
var wsoPanel = require("panel").Panel({
  width: 350,
  height: 500,
  contentURL: data.url("myHTML.html"),
  contentScriptFile: data.url("myJS.js")
});
```

When I set the "width" and "height" propertites, the background of the panel is transparent. When I delete these two properties, the background has the color defined in the CSS of the myHTML.html file.

Any ideas why that happened?

thank,
Andre

---

### Post by hickhack on 2012-08-10
Nobody?

---

