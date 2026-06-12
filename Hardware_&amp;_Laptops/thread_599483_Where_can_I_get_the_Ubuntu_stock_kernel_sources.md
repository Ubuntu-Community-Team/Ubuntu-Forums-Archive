---
title: "Where can I get the Ubuntu stock kernel sources"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by t0medwards on 2007-11-01
Hello,

For various reasons my laptop doesn't like the stock Ubuntu kernel. Instead I have to recompile the rtl139too driver with different options. This is all fine and dandy, and in the past (fiesty) I have used the linux-source package which seemed to come with all the extra modules and restricted sections of code that linux-image-generic came with.

I have just upgraded to Gutsy and am looking to recompile my kernel based on the settings of the stock gutsy kernel, however this is proving difficult as things like intel_hda audio and ipw3945 are not longer in this package.

Do any of you know where I might find the set of patches applied to the linux-source or linux-restricted-modules (which only contains the ipw3945 microcode in source package) that the Ubuntu kernel team are using? Is it even available or will I have to construt this stuff myself?

Cheers,

Tom

---

