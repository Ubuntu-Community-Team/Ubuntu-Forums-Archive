---
title: "PCI V92 modems in Linux, buying &amp; using."
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by Zerksis on 2005-09-04
There are many people who still have to use 'dial-up' for internet access.
For Linux the profusion of Winmodems has created support problems, first
time users find this a bit of a mine-field.

If you;-

   [i]want to minimise on the number of wires around your PC
   are not too concerned about using some CPU resources (speed)
   don't want to use an old, bulky serial modem
   don't want to shell out for a new USB modem (may still be winmodem!)[/i]
   
Then you should know that you can buy a brand new Intel 536EP chipset 
PCI modem, for £5.88 (GB pounds including UK VAT tax) from;-

  [http://daintyinfo.co.uk/catalog/product_info.php?cPath=27&products_id=230&osCsid=a668d65d08bb3da1f04c8e607620cb14](http://daintyinfo.co.uk/catalog/product_info.php?cPath=27&products_id=230&osCsid=a668d65d08bb3da1f04c8e607620cb14)

As your OS is free, an outlay of less than £6 is considered quite modest.

Intel provides good support for this chipset and Linux, see their website 
for Linux drivers at -


  [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)


The writer has tried these modems on 3 different motherboards all running 
Ubuntu Linux.  All worked with both Ubuntu Linux and Windows XP.
In one case an early 536 modem card with a single pin cutout* (5V I/O?) was 
swapped out with a £5.88 card which has two pin cutouts. The low cost card 
worked without any problem.  

If you have ever lost a modem during a nearby lightning strike then the ability
to replace the modem, with no uninstall/install & configure, is pretty useful.
    
Some distibutions will recognise and automatically configure PCI modems with
the Intel 536EP chipset, e.g. xandros 3.01 and (it is reported) SuSE Linux


To sum up - some PCI modems work well in Ubuntu, they don't cost a lot, plus
Ubuntu has an Intel 536 'how to' Wikipage at;-

  [https://wiki.ubuntu.com/IntelFiveThreeSixEPModemHowto?highlight=%28fivethreesix%29](https://wiki.ubuntu.com/IntelFiveThreeSixEPModemHowto?highlight=%28fivethreesix%29)


***PCI notes:**
PCI migrated from 5V I/O drivers in the original PCI implementation to 3.3V 
I/O drivers in PCI Revision 2.2. For the same data rate, lower voltage means 
lower power consumption. Lower voltage also enables higher speed at the same 
power level, and it allows for the use of more advanced IC processing with 
lower parasitic capacitances and faster transistors.

How do 5 and 3.3V systems coexist? 
To accommodate two I/O driver voltages, the PCI standards committee defined one 
edge connector with two key positions: one for 3.3V operation and the other for 
5V operation. They similarly keyed adapter cards, with a cutout in the 5V location 
for 5V boards and a cutout in the 3.3V location for 3.3V boards. 

Boards that could operate at both 3.3 and 5V had two cutouts and could therefore 
fit into either connector.  

*see full article at;-*  (may get moved)

 [http://www.edn.com/article/CA472831.html](http://www.edn.com/article/CA472831.html)
 
 [i]other help[i]
 [http://www.ubuntuforums.org/showthread.php?t=37465](http://www.ubuntuforums.org/showthread.php?t=37465)

---

