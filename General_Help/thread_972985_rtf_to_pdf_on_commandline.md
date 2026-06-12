---
title: "rtf to pdf on commandline"
date: 2008-11-06
forum: General Help
---

### Post by taavi on 2008-11-06
Hi,

I would like to convert .rtf documents to .pdf... Is there some kind of library or command line application doing that? I googled it, but result were outdated or garbish, maybe I asked it wrong.

Do you know any option?

Thanks!

---

### Post by .nedberg on 2008-11-06
Have a look here:
[http://www.oooforum.org/forum/viewtopic.phtml?t=3772](http://www.oooforum.org/forum/viewtopic.phtml?t=3772)

I use it to convert doc, xls and ppt into pdf. I am sure it would work with rtf too.

---

### Post by bapoumba on 2008-11-06
Moved to General Help.

---

### Post by taavi on 2008-11-12
Thank you for help, I'll look into it, but it seems overkill at start, but that's not so biggie...

---

### Post by kaibob on 2008-11-12
You can convert RTF documents to PDF format by way of a two-step process. Post 3 in the following thread contains both a suggested command-line and shell script:

[http://ubuntuforums.org/showthread.php?t=974961&highlight=rtf+pdf](http://ubuntuforums.org/showthread.php?t=974961&highlight=rtf+pdf)

If you experience issues with unrtf, you can substitute ted, which has a GUI but works well as a command-line tool:

[http://manpages.ubuntu.com/manpages/gutsy/man1/Ted.html](http://manpages.ubuntu.com/manpages/gutsy/man1/Ted.html)

---

### Post by taavi on 2009-01-07
Thank you for replies. I got it working with Openoffice macros. I include it in attachments.

01. Edit your *~/.openoffice.org2/user/basic/Standard/Module1.xba* file. It must look like file in attachment: Module1.xba.txt
02. Make a script file like attachment file2pdf.txt.
03. Run script with an document file as an argument.

Current macro only supports doc, xls and ppt files, but it's trivial to make it support any filetype Openoffice can handle. 

Please note that these scripts/macros hasn't been written by me, I only share them with you. As there were no copyright notes, I thought it's allowed to put them up here. All thanks to Kevin Martin from linux.derkeiler.com mailing lists: [http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-06/msg00561.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-06/msg00561.html)

Hope they work for you.

---

