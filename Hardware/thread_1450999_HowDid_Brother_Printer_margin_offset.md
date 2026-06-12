---
title: "HowDid: Brother Printer margin offset"
date: 2010-04-09
forum: Hardware
---

### Post by dpj on 2010-04-09
Despite my low post count, I'm actually pretty knowledgeable with Linux, having used Debian for at least 10 years now. I've also had to solve all sorts of problems over the years and I keep thinking I should do something about sharing this knowledge. Most of the solutions are gleaned from sites like this, but often I've had to assemble them from more than one source, and the following is such an example.

I recently bought a Brother MFC-465CN multifunction network printer, having done so because it has Linux drivers available as well as decent-sized ink cartridges.

I followed the instructions on the Brother Solutions page:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

and that all worked, but when it came to printing I noticed that the output was not centred on the page.

Specifically, the output was too close to the left edge and some of the output was cut off at the top, while there was excess space at the right and bottom. I could fix this manually by adjusting the margins, but that's a bit annoying and not user-friendly. Note that many people who apparently have this problem are using A4 paper whereas the printer is set to use US Letter; this is a separate problem for which there is another solution:

[http://solutions.brother.com/linux/sol/printer/linux/printsetlpr.html](http://solutions.brother.com/linux/sol/printer/linux/printsetlpr.html)

The as-printed output had a top margin of 5 mm, a left margin of 5 mm, a right margin of 12 mm and a bottom margin of 16 mm.

My first idea was to modify the driver's imageable area and modify the printer in CUPS to use the modified driver. That worked - once. I'm not sure why, but after that the output continued as before, even though the margins in the print dialogue were now asymmetrical. It turns out that the cupswrapper way that Brother has supplied their drivers contains a second version of the driver. I wasn't pleased about this and modifying the imageable area is a bit of a hacky way of fixing what is an offset problem anyway. In my searches I had found reference to altering the offset at the command line using lpr and a file.

So here's how you do it:

Create a text file with the following content:

> 
%-12345X@PJL 
@PJL DEFAULT XOFFSET=-90
@PJL DEFAULT YOFFSET=-117

%-12345


I named it 'BrotherPrinterOffset.prn' and saved it in /usr/local/Brother/Printer/mfc465cn/

I don't know what measuring system is being used, or even where the point of reference is, but they have a ratio of about ~11.7:1 mm, so the 90 X offset represents an offset of about 7.5 mm and the -117 Y offset of about 10 mm. Modify as needed/desired.

Next I had to apply it using lpr. To find out the name the printer I issued the command lpq:

> 
# lpq


On my Kubuntu box this returned 'Brother_MFC-465CN', which I used thusly:

> 
# lpr -P Brother_MFC-465CN -o raw /usr/local/Brother/Printer/mfc465cn/BrotherPrinterOffset.prn


After that I restored the printer to its original driver in CUPS and printed a test page and it came out centred.

I hope this helps someone.


Keywords: Brother Printer MFC-465CN offset margin alignment

---

### Post by Lovegain on 2011-05-20
Awesome! Thanks.

---

### Post by Alfiran on 2011-08-29
Hello,

Unfortunately it didn't work in my Lucid Lynx.
Eventually I found in Brother's the solution for my case:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#147](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#147)

The "paper size" parameter explained in the web doesn't exit so I decided to change the parameter "PaperType" in the file:

/usr/local/Brother/Printer/mfc465cn/inf/brmfc465cnrc

It was stated as PaperType=letter so I changed it to PaperType=A4.
It worked perfectly.

---

### Post by idiosynthetic on 2011-10-19
Alfiran, perfect, thank you!

---

