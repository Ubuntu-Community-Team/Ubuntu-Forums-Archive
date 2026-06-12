---
title: "HP Printer driver issues in Maverick"
date: 2010-11-27
forum: Hardware
---

### Post by shane2peru on 2010-11-27
Ok, I had my printer setup with Lucid, and didn't have a problem.  I have a HP Laserjet 1022n it is setup/plugged in directly to my router.  In Lucid I didn't have a problem.  Here is the issue now.  
I know the IP address and set it up as AppSocket/HP JetDirect and plugin the IP address.  When I get to the driver page I have 4 to choose from and am not sure what the difference is or what to pick.  Here are my 5 choices, and a few notes that I have made about them.

```
Foomatic/foo2zjs
```
With this one I can print via command line, however GUI (OO.o and evince) printing is problematic.  Also lacking the options when I select Print -> Properties -> Device (tab)  it is lacking the media type.



```
hpjis pcl3 3.10.6
```
I can print via GUI but command line printing doesn't work, just sets there processing.  GUI printing the printer just shuts off??? No lights lit, I have to shut it off and turn it back on, odd.



```
hpijs zjs 3.10.6
```
Not sure.



```
pcl, hpcups 3.10.6
```
Not sure.



```
zjs hpcups 3.10.6
```
Not sure.



I really don't know what all these are, or what the differences are.  If anyone has info, links or something I would be interested in knowing the difference, and what is the best.  I print both with GUI and command line often.  Thank you for ANY help you can offer because this is really a frustration for me.

Shane

---

### Post by gabhla on 2010-11-27
Just went through a very similar experience.  I have the HP Laserjet 1020, which is very similar to yours and uses the same driver.  I got mine to work by installing hplip, it's in the repo's, then, from the command line, "hp-setup -i".

---

### Post by shane2peru on 2010-11-28
> **gabhla said:**
> Just went through a very similar experience.  I have the HP Laserjet 1020, which is very similar to yours and uses the same driver.  I got mine to work by installing hplip, it's in the repo's, then, from the command line, "hp-setup -i".

Thank you Thank you Thank you!!!  :popcorn:  After running through that now I think I did do that on Lucid.  I certainly wouldn't have remembered that!  Thanks a bundle!  I will try this out for a few days before marking this solved.

---

### Post by shane2peru on 2010-12-06
Well, I thought that had fixed it, but problems trying to print today.  It is really weird and very annoying.  It did print fine for a while with that setup, however with that setup I can't select the media type (thick stock) which them messes things up when printing on thick stock.  This is still a problem.

Shane

---

