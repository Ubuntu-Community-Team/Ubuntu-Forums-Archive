---
title: "Problems with OOo in Ubuntu 8.04"
date: 2008-11-16
forum: General Help
---

### Post by kjmorris on 2008-11-16
Greetings - I recently installed Ubuntu 8.04 and have encountered two problems with the Ubuntu/Debian version of OOo that is included and that I need to use daily.

1. Whenever I try to open a .txt file in OOo, it tries to open it as a spreadsheet in Calc! I either have to copy-and-paste the text into a new document or use a several-step workaround that was provided to me on another list. Both are very annoying, since I work in OOo and text editors all day. The only other suggestion that I have received is to replace the Ubuntu version of OOo with a downloaded version from the OOo website. Is this what I should do? As is, it's a big step backward for me at at time when I need most to use OOo efficiently.

2. FONTS: My default font is Times New Roman and sometimes Garramond. I need both for work. They don't seem to be available in the Ubuntu version of OOo. Where and how can I get them and install them?

TIA kjmorris

---

### Post by 73ckn797 on 2008-11-16
> **kjmorris said:**
> 1. Whenever I try to open a .txt file in OOo, it tries to open it as a spreadsheet in Calc! I either have to copy-and-paste the text into a new document or use a several-step workaround that was provided to me on another list. Both are very annoying, since I work in OOo and text editors all day. The only other suggestion that I have received is to replace the Ubuntu version of OOo with a downloaded version from the OOo website. Is this what I should do? As is, it's a big step backward for me at at time when I need most to use OOo efficiently.

Can you right click the file and tell it to open with Writer? With a right click select properties and designate the open with default.

> **kjmorris said:**
> 2. FONTS: My default font is Times New Roman and sometimes Garramond. I need both for work. They don't seem to be available in the Ubuntu version of OOo. Where and how can I get them and install them?

Look in Synaptic for msttfonts and install that for this issue.

---

### Post by kjmorris on 2008-11-16
> **73ckn797 said:**
> Can you right click the file and tell it to open with Writer? With a right click select properties and designate the open with default.

If I open Nautilus and right-click on a .txt file, I can choose to open it with OOo Writer and it works. But if I simply try to open a .txt file in OOo as I have been doing for ages, I no longer have the option - it simply opens in Calc. I don't see any place where I can set Writer rather than Calc as the default for opening .txt files.

> **73ckn797 said:**
> Look in Synaptic for msttfonts and install that for this issue.

I did a search in Synaptic and it didn't find msttfonts.

Thanks. kjmorris

---

### Post by 73ckn797 on 2008-11-16
> **kjmorris said:**
> If I open Nautilus and right-click on a .txt file, I can choose to open it with OOo Writer and it works. But if I simply try to open a .txt file in OOo as I have been doing for ages, I no longer have the option - it simply opens in Calc. I don't see any place where I can set Writer rather than Calc as the default for opening .txt files.



I did a search in Synaptic and it didn't find msttfonts.

Thanks. kjmorris


Sorry, look for msttcorefonts. I am running 8.10 and it is in Synaptics. Make sure you are looking at all available packages (universe, multiverse) and not just supported packages.

---

### Post by kjmorris on 2008-11-16
> **73ckn797 said:**
> Look in Synaptic for msttfonts and install that for this issue.

OK, I found and installed msttcorefonts and that seems to have worked. I now have Times New Roman (but not Garramond, that I need less often).

When installing msttcorefonts, I got the following message:

"Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts.

The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf.

For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required."

Is this something that I need to be concerned about?

Thanks.  kjmorris

---

### Post by 73ckn797 on 2008-11-16
I have not encountered that message that I remember so do not know what to say about that.

Look around via search on the forums for the other font/info. 

Check out [https://help.ubuntu.com](https://help.ubuntu.com) and [http://www.ubuntu.com/community](http://www.ubuntu.com/community)

I know there are other ways to add fonts but I have not had to do that.

---

