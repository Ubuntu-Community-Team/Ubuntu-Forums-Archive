---
title: "Lexmark Printer Help"
date: 2010-01-19
forum: Hardware
---

### Post by K-Dogg on 2010-01-19
I'm not sure If I'm posting this in the right place but I'm having a problem installing a Lexmark x4650 I believe on my brother-in-laws pc. I have the driver disc which I know is for windows but I was wondering if there was anything that I could do with the drivers on the disc to make it work? 

[IMG]http://www1.lexmark.com//content/x4650/x4650_large.png[/IMG]

---

### Post by studmf on 2010-01-19
Openprinting updates printer drivers available for Linux.  I have the same printer....its a paperweight in linux.  I have to print in virtalbox guest (Win7).
> OpenPrinting database - Printer: Lexmark X4650
    [Home]("http://openprinting.org/") **:** [Database]("http://openprinting.org/database.html") **:** [Printers]("http://openprinting.org/printer_list.cgi") **:** [Lexmark]("http://openprinting.org/printer_list.cgi?make=Lexmark") **:** X4650[FONT=ms sans serif, helvetica][SIZE=+1]Lexmark [X4650]("http://www.lexmarkonline.co.uk/product_info.php/info/p1602_Lexmark-X4650.html?XTCsid=ed3b1de118129b795f2625818e21444c")[/SIZE][/FONT] [FONT=ms sans serif, helvetica]Color inkjet printer, max. 4800x1200 dpi, this is a [COLOR=red]Paperweight[/COLOR][/FONT] [FONT=ms sans serif, helvetica][IMG]http://openprinting.org/linuxno.png[/IMG][/FONT] [[IMG]http://twitter.com/favicon.ico[/IMG]]("http://search.twitter.com/search?q=Lexmark%20X4650%0AColor%20inkjet%20printer%2C%20max.%204800x1200%20dpi%2C%20this%20is%20a%20Paperweight%20%09%0A")[[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=Lexmark%20X4650%0AColor%20inkjet%20printer%2C%20max.%204800x1200%20dpi%2C%20this%20is%20a%20Paperweight%20%09%0A")[[IMG]http://static.smarterfox.com/media/wiki-favicon-sharpened.png[/IMG]]("http://smarterfox.com/wikisearch/search?q=Lexmark%20X4650%0AColor%20inkjet%20printer%2C%20max.%204800x1200%20dpi%2C%20this%20is%20a%20Paperweight%20%09%0A&locale=en-US")[[IMG]http://static.smarterfox.com/media/popup_bubble/oneriot-favicon.ico[/IMG]]("http://www.oneriot.com/search?p=smarterfox&ssrc=smarterfox_popup_bubble&spid=8493c8f1-0b5b-4116-99fd-f0bcb0a3b602&q=Lexmark%20X4650%0AColor%20inkjet%20printer%2C%20max.%204800x1200%20dpi%2C%20this%20is%20a%20Paperweight%20%09%0A")

---

### Post by studmf on 2010-01-19
[HERE]("http://openprinting.org/printer_list.cgi?make=Lexmark") is the link for Lexmark printers

---

### Post by K-Dogg on 2010-01-19
so in other words I'm outta luck at the moment unless I setup a virtual box. Thanks for the fast reply.

---

### Post by Sef on 2010-01-19
> so in other words I'm outta luck at the moment unless I setup a virtual box. Thanks for the fast reply.

The other option is to get an old PIII with windows on it and set it up as a print server.

---

### Post by K-Dogg on 2010-01-22
I might sound a little dumb now but how would I go about setting up a virtual box and make it print?

---

### Post by studmf on 2010-01-22
You would have to install VirtualBox, then install windows as the guest OS.  There are a lot of guides explaining exactly how to do it if you are unsure.  It is really pretty simple, you can then share files between OS's via share folders and are supposed to be able to copy and paste between the two; however, this feature does not seem to work for me.  Once you have your windows OS installed, simply install the Printer as you normally would and voila.
 
Virtualbox is available from the repositories; however if you go directly to virtualbox site there is a more current version (at least there was) and it also tells you what deb to add to your source.list.  Ensure you allow VB to build kernal during setup, it will seem like the PC gets locked up, just leave it alone for a few minutes while it works.

---

### Post by K-Dogg on 2010-01-22
ok thank you very much. I shall try that later.

---

