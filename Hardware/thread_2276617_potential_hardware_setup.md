---
title: "potential hardware setup"
date: 2015-05-03
forum: Hardware
---

### Post by mattdawolf on 2015-05-03
I plan on building the following system.

 option1 [[CASE1 $400] IPC-622 - 6U 20-Slot Rackmount Chassis Supporting Quad-System and Redundant Power Supply - Advantech]("http://www.advantech.com/products/1-2JKDA1/IPC-622/mod_99EB6072-12B1-47B7-A876-E727D4381391.aspx") 
[URL="http://buy.advantech.com/PCE+7B17+00A1E/PCE+7B17+00A1E/model-PCE-7B17-00A1E.htm?gclid=CjwKEAiAsJanBRCgnpfa0orvyz4SJAAbxEq-5kW73fb30Bc7CUUAtcnoEd1sVDCYxWx57QhM5kWOHRoCb0Pw_wcB"]
[BACKPLANE1 $1200] PCE-7B17-00A1E-17-Slot Server Grade Backplane with Gen 3 PCIe x8, PCIe x4[/URL] 
 [URL="http://www.atacomipc.com/program/print_ipc_spec.cgi?Item_code=IMP3_PORT_XS_01"]
[SBC1] ($500) {16gb ram MAXIMUM} Portwell AB1-3600 ROBO-8110VG2AR Intel Core i3/ Xeon E3-1200 C206, DDR[/URL] 

 [[CPU] $350 {spec MAXIMUM} Intel Xeon E3-1270 V2 Ivy Bridge 3.5GHz (3.9GHz Turbo) LGA 1155 69W Server Processor BX80637E31270V2 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117283&cm_re=xeon-_-19-117-283-_-Product") 

The GPU would be 8 of these [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121839](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121839)

and my question would be, would doing dual 4-way sli even be feasible?

---

### Post by dino99 on 2015-05-04
4 way sli is way worst than 4 single cards

---

### Post by tokyobadger on 2015-05-05
^^what he said... even in windows, SLI doesn't scale well unless the software (usually games) is optimized, and even then the gains over 2 cards are debatable. And then there's the additional 2x 4-way SLI - not seeing much documentation for that. Add to that that SLI in linux has not been a focus of nvidia's for many years, most people are saying save the money and get the best single GPU you can.

However, it does depend what you want to do with the build, if it's not games then I'd look into whether SLI is what you need for video editing, render farm, *coin-crunching - I won't offer an opinion as I do none of those. All I can tell is that aside from costing you a bunch on the build, it'll also cost you a bunch to run too in terms of power.

---

