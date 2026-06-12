---
title: "HP PCS 1350 All-In-One driveing me crazy"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by ZakSmith on 2007-04-23
I can not get this printer to work (I am very new to Linux). I had an easier time with my wireless card :) . Does anyone have a fairly simple way of getting this printer to work. All I have found are general command line guides that say things like "use this command for this dist and this command for this dist". It has me very confused.

Thanks,

Zak

---

### Post by blitzer on 2007-04-23
Hello ZakSmith,

The good ole Add/Remove might have what you need:

To the upper right (Show) click the drop down box and select Supported Ubuntu Applications.  On the left pane click OTHER >HPLIP Toolbox

HPLIP Toolbox
HP Linux Printing and Imaging System (HPLIP) 
The HP Linux Printing and Imaging System provides full support for printing on most HP SFP (single function peripheral) inkjets and many LaserJets, and for scanning, sending faxes and for photo-card access on most HP MFP (multi-function peripheral) printers.
HPLIP is composed of:
&#8226; System services to handle communications with the printers
&#8226; HP CUPS backend driver (hp:) with bi-directional communication with HP printers (provides printer status feedback to CUPS and enhanced HPIJS functionality such as 4-side full-bleed printing support)
&#8226; HP CUPS backend driver for sending faxes (hpfax:)
&#8226; HPIJS Ghostscript IJS driver to rasterize output from PostScript(tm) files or from any other input format supported by Ghostscript, and also for PostScript(tm) to fax conversion support (HPIJS is shipped in a separate package)
&#8226; Command line utilities to perform printer maintenance, such as ink-level monitoring or pen cleaning and calibration
&#8226; GUI and command line utility to download data from the photo card interfaces in MFP devices
&#8226; GUI and command line utilities to interface with the fax functions
&#8226; A GUI toolbox to access all these functions in a friendly way
&#8226; HPAIO SANE backend (hpaio) for flatbed and Automatic Document Feeder (ADF) scanning using MFP devices
USB, JetDirect (network) and parallel-port devices are supported.

---

