---
title: "Dymo Label Printer (ppd library error, maybe?)"
date: 2018-07-26
forum: Hardware
---

### Post by toddje on 2018-07-26
Running a clean install of ubuntu desktop 18.04.1
I have a Dymo LabelWriter 450 Turbo and I've got (I think) everything I need downloaded and installed.   ./configure runs fine (end of configure.log shows exit 0) on the dymo 1.4.0.5 software, but I guess I'm missing some piece of printer drivers, because when I got to make, I start getting errors and ultimately it fails.   

(Incidentally, I set up an HP laserjet printer on this same machine without problem today as well.)

Here's the start of my errors.  I imagine someone who knows more about printing will be able to help quite quickly, but if not I can post more of the error...
Thanks in advance for your help!


In file included from raster2dymolw.cpp:37:0:
../common/CupsFilter.h: In member function &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*)&#8217;:
../common/CupsFilter.h:218:3: error: &#8216;ppd_file_t&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
   ^~~~~~~~~~
../common/CupsFilter.h:218:3: note: suggested alternative: &#8216;cups_file_t&#8217;
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
   ^~~~~~~~~~
   cups_file_t
../common/CupsFilter.h:218:15: error: &#8216;ppd&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
               ^~~
../common/CupsFilter.h:218:21: error: there are no arguments to &#8216;ppdOpenFile&#8217; that depend on a template parameter, so a declaration of &#8216;ppdOpenFile&#8217; must be available [-fpermissive]
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ^~~~~~~~~~~
../common/CupsFilter.h:218:21: note: (if you use &#8216;-fpermissive&#8217;, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
../common/CupsFilter.h:228:3: error: there are no arguments to &#8216;ppdMarkDefaults&#8217; that depend on a template parameter, so a declaration of &#8216;ppdMarkDefaults&#8217; must be available [-fpermissive]
   ppdMarkDefaults(ppd);
   ^~~~~~~~~~~~~~~
../common/CupsFilter.h:234:7: error: there are no arguments to &#8216;ppdMarkOption&#8217; that depend on a template parameter, so a declaration of &#8216;ppdMarkOption&#8217; must be available [-fpermissive]
       ppdMarkOption(ppd, Options[i].name, Options[i].value);

---

