---
title: "Unable to install Fuji Xerox DP204a"
date: 2008-05-25
forum: Hardware
---

### Post by timace on 2008-05-25
Hi there,

I'm having problems installing my Fuji Xerox DP204a printer (connected via ethernet to my router)

When I go to use the ppd driver (supplied by the manufacturer), this is the error generated:

Failed to read PPD file.  Possible reason follows:
/home/timb/.gvfs/print$ on poknat/w32x86/fxdocuprint_204a5961/FP204A.PPD: FAIL
      **FAIL**  Unable to open PPD file - Missing PPD-Adobe-4.x header on line 1.
                REF: Page 42, section 5.2.
        WARN    File contains a mix of CR, LF, and CR LF line endings!
        WARN    Non-Windows PPD files should use lines ending with only LF, not CR LF!

Any idea how I can get around this?

Thanks in advance :)

---

### Post by timace on 2008-05-26
Anybody? :)

---

### Post by cogitordi on 2008-06-14
> **timace said:**
> 
When I go to use the ppd driver (supplied by the manufacturer), this is the error generated:

Failed to read PPD file.  Possible reason follows:
/home/timb/.gvfs/print$ on poknat/w32x86/fxdocuprint_204a5961/FP204A.PPD: FAIL
      **FAIL**  Unable to open PPD file - Missing PPD-Adobe-4.x header on line 1.
                REF: Page 42, section 5.2.
        WARN    File contains a mix of CR, LF, and CR LF line endings!
        WARN    Non-Windows PPD files should use lines ending with only LF, not CR LF!

Same problem here with a Brother HL-2070N. I did however use a text editor to convert the Windows line endings to UNIX.

---

