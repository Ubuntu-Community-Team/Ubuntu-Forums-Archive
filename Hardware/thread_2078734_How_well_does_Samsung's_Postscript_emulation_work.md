---
title: "How well does Samsung's Postscript emulation work?"
date: 2012-10-31
forum: Hardware
---

### Post by domgross on 2012-10-31
Hi,

Does anybody have experience with the Linux drivers / PS emulation of Samsung office laser printers (e.g. ML-5010ND)? 
Looking into the ppds in the Samsung "unified" driver it seems the driver for the (ML-451x / ML-5010N) relies on the printers PS emulation. 

Since we had some really bad results with Kyocera's linux drivers / PS emulation (see below) I would really appreciate some input on how well the Samsung Linux drivers / PS emulation work or recommendations of other printers in the same range with good PS emulation. 


The current setup consists of a CUPS server, ubuntu clients and a couple of Kyocera printers. Thanks to Kyocera's bad Postscript emulation the result is as follows:

[LIST]
[*] using the official ppds (or windows non-KX driver) the printers often stop or mess up the output even on simple documents (research papers and book chapters with text and formulas) 

[*] Using a PCL printer driver in CUPS and PCL emulation on the Printer (or windows KX drivers) gives correct output but slows 
a 26 ppm printer down to around 4 ppm.
[/LIST]

---

