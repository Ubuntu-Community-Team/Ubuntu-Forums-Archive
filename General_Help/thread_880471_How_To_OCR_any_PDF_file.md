---
title: "How To: OCR any PDF file"
date: 2008-08-05
forum: General Help
---

### Post by RequinB4 on 2008-08-05
As anyone who has tried knows, using optical character recognition on pdf files can be confusing, especially since [Tesseract]("http://code.google.com/p/tesseract-ocr/"), repeatedly hailed as the best free ocr software can only do *tif files.

**Step 1: Install needed packages**
```

sudo apt-get install tesseract-ocr tesseract-ocr-eng xpdf-reader xpdf imagemagick xpdf-utils

```

[SIZE="2"]Side Note: You will need to install language packages for tesseract for every other language you wish to use.  For example, package tesseract-ocr-fra allows you to ocr the french language.  Check synaptic package manager[/SIZE]

**Step 2: See if you actually need ocr**

xpdf-utils (which you just installed) provides a pdftotext utility:
```
pdftotext
```
If it works, congratulations and don't move on :)

**Step 3: OCR'd**

The following shell script will attempt to ocr your file.  I suggest placing it somewhere in your $PATH so you can run it from the same directory as the pdf file and not have weird filenames.

**NOTE: This program works by converting each page of the PDF file into a 100MB TIFF image.  That means a temporary 100MB increase of hard drive usage per page in your pdf while the program is running.**  If it's an issue, this can be decreased/changed by editing the shell script - either decrease the quality number in pdftoppm or make it do only a few pages at a time - check man pdftoppm

```

#!/bin/sh
mkdir tmp
cp $@ tmp
cd tmp
pdftoppm * -f 1 -l 10 -r 600 ocrbook
for i in *.ppm; do convert "$i" "`basename "$i" .ppm`.tif"; done
for i in *.tif; do tesseract "$i" "`basename "$i" .tif`" -l nld; done
for i in *.txt; do cat $i >> ${name}.txt; echo "[pagebreak]" >> pdf-ocr-output.txt; done
mv pdf-ocr-output.txt ..
rm *
cd ..
rmdir tmp

```

**Usage:**
1) Copy the script into gedit or your favorite text editing program and save it.
2)
```
cd /path/to/saved/file/
chmod +x filename
```
3) Run the script: If it is saved in your $PATH, just type the filename in the console, followed by the name of the file you wish to ocr.  Otherwise, you have to cd to the /path/to/saved/file and ```
./filename "PDF file you wish to ocr"
```

Edit: Moving to tutorials and tips -my bad

---

### Post by waspinator on 2009-04-28
is there a way to integrate the ocr layer back into the pdf so that you create a searchable pdf instead of a seperate text file?

---

### Post by nortexoid on 2009-09-30
That's what I'm interested in.

---

### Post by userid on 2009-12-15
Probably via openoffice.org 3.0 / editable pdf?

Thanks for the excellent script btw!

> pdftoppm * -f 1 -l 10 -r 600 ocrbook

Seems like its limited to the first 10 pages? I also think the quality of the ppm is rather high!

---

### Post by AlwaysLearning on 2010-01-04
> **userid said:**
> Probably via openoffice.org 3.0 / editable pdf?

Alright, you've got my attention here. Karmic has OO.org v3.1.1 now and yet in Writer I'm still only seeing an "Export as PDF" option... is there extra-magic (such as Extensions) that you need to edit an existing PDF to insert the text layer?

---

### Post by nortexoid on 2010-01-27
I tried the script out and it doesn't always work. The only usable solution I've found--and it's hardly a solution!--is to run a VM of Windows and Acrobat Standard/Pro!

Pretty lame.

---

### Post by khaeru on 2010-02-05
> **nortexoid said:**
> Pretty lame.

Well, complaining about free scripts is also "pretty lame."

RequinB4, I edited your script a bit. It works great! For futher improvement, to cut down on the disk usage one could use "pdfinfo" to get the number of pages in the file and extract them one at a time using the same page for the -l and -f parameters to pdftoppm.

Also note if you want to run this, all you really need to install are tesseract-ocr-[LANG] and imagemagick (tesseract-ocr is a dependency of each of the individual tesseract language packages). Change "-l eng" in the file to match the tesseract language you've installed/want to use.
```

#!/bin/sh
SCRIPT_NAME=`basename "$0" .sh`
TMP_DIR=${SCRIPT_NAME}-tmp
OUTPUT_FILE=${SCRIPT_NAME}-output.txt

mkdir $TMP_DIR
cp $@ $TMP_DIR
cd $TMP_DIR

pdftoppm -r 600 * ocrbook

for i in *.ppm
do
  BASE=`basename "$i" .ppm`
  convert "$i" "${BASE}.tif"
  tesseract "${BASE}.tif" "${BASE}" -l eng
  cat ${BASE}.txt | tee -a $OUTPUT_FILE
  echo "[pagebreak]" | tee -a $OUTPUT_FILE
  rm ${BASE}.*
done

mv $OUTPUT_FILE ..
rm *
cd ..
rmdir $TMP_DIR

```

---

### Post by clevertomato on 2010-02-08
I could use some clarification. I'd like to be able to scan documents and end up with a text-based PDF (searchable, selectable), but when I read "insert text layer" in this thread, I am a little lost.

---

### Post by Koppie on 2010-02-11
Gscan2pdf is GREAT.  It installs pretty much every package you need at once, although I also had to install the tesseract English module.

---

### Post by clevertomato on 2010-02-12
More clarification, please? Bear with me if this seems elementary.

Let's say I type a document in Open Office and export to PDF. When I open the PDF, AFAIK, I don't see a "picture" of the text with a hidden text layer that can be indexed. It appears to be ACTUAL text that I'm looking at. I can select text, search text, etc, right there in the document that appears before me.

What I'm reading so far about these OCR tools is that I'm still left with an IMAGE of the page of text, but with an extra hidden layer of actual text somewhere that can be searched. Am I understanding this correctly? Is there no way to use OCR to end up with essentially the same kind of PDF that I get when I export a word processing document to PDF? I don't want both an image of text and actual text hidden somewhere behind it.

---

### Post by khaeru on 2010-02-14
@shawnboy: generally that's correct. When you export from OpenOffice, the PDF contains an embedded font and each character in the text is displayed using that font. Your PDF viewer generates the "picture" on-the-fly, at whatever resolution you like.

Optical Character Recognition, as the name implies, tries to determine characters from shapes in an image. Some tools will bundle these guesses in a PDF, hidden behind the original image. That's not too hard of a problem for a computer.

Recognizing the actual *font* and reconstructing the text layout that produced an image would be much harder. There are tools like What The Font ([http://new.myfonts.com/WhatTheFont/](http://new.myfonts.com/WhatTheFont/)) that will give you many (sometimes mediocre) guesses at what fonts appear in an image. But WTF is backed by a very large font library, and it's a proprietary tool. There is no comparable Free equivalent that I know of, and certainly no all-in-one tool that:
[list=1]
[*]performs OCR,
[*]performs font recognition,
[*]reconstructs the layout of an original document, and finally
[*]generates a document that closely resembles the original scan.
[/list]

Until some saviour codes a program that does all this, #2 and #3 have to be done manually.

---

### Post by clevertomato on 2010-02-15
khaeru: Thanks for the clarification. There's apparently more going on behind the scenes that I imagined. Ignorance is bliss.

---

### Post by texaswriter on 2010-03-07
> **khaeru said:**
> @shawnboy: generally that's correct. When you export from OpenOffice, the PDF contains an embedded font and each character in the text is displayed using that font. Your PDF viewer generates the "picture" on-the-fly, at whatever resolution you like.

Optical Character Recognition, as the name implies, tries to determine characters from shapes in an image. Some tools will bundle these guesses in a PDF, hidden behind the original image. That's not too hard of a problem for a computer.

Recognizing the actual *font* and reconstructing the text layout that produced an image would be much harder. There are tools like What The Font ([http://new.myfonts.com/WhatTheFont/](http://new.myfonts.com/WhatTheFont/)) that will give you many (sometimes mediocre) guesses at what fonts appear in an image. But WTF is backed by a very large font library, and it's a proprietary tool. There is no comparable Free equivalent that I know of, and certainly no all-in-one tool that:
[LIST=1]
[*]performs OCR,
[*]performs font recognition,
[*]reconstructs the layout of an original document, and finally
[*]generates a document that closely resembles the original scan.
[/LIST]

Until some saviour codes a program that does all this, #2 and #3 have to be done manually.

Not sure what angle you are talking on, but there are several programs that do ALL 4 of those. 

1) Adobe Acrobat Professional: by no means the best because it requires a VERY HIGH RESOLUTION base image. You can take PDF's that are images and ocr them. You can make pdf's [ocr them] from stock images... 

2) Abby FineReader [and there's a pro version as well]: This is actually one of the best there is. It's faster and can scan more accurately with a substantially lower resolution image. 

3) IRis

4) Verus

5) Nuance omnipage... this is very expensive

---

### Post by khaeru on 2010-03-07
The capital 'F' in 'Free' meant I was talking about free and open source software, of the kind that's included in Ubuntu.

---

### Post by Cedders on 2010-04-15
Thanks for the pointers/script, but for some reason I get terrible results with Tesseract (just symbols and perhaps an occasional word fragment).  Doing it directly from the PPM using ocrad -l2 seems to produce better results.  It could be the (dithered) scan quality.  Any ideas how to rectify?

ocrad/karmic uptodate 0.17-4
tesseract-ocr/karmic uptodate 2.03-2ubuntu1
tesseract-ocr-deu/karmic uptodate 2.00-1
tesseract-ocr-eng/karmic uptodate 2.00-1

BTW convert also has a rotation option which may be useful:
convert -rotate -90

I also think 300dpi should be sufficient.

---

### Post by jfouse on 2010-04-15
Here's an updated version.

* Using khaeru's suggestion re: pdfinfo to do one page at a time, reducing overall drive space needed
* More explicitly looping over each of multiple named files
* Integrated an optional "-r <num>" param for rotating, if you know the pages need to be rotated.  This takes a degree measurement, and is passed directly to the -rotate param of convert.
* Cleanly handles filenames with spaces.
* Put the desired tesseract language in its own var up front so it's easily found and modified if needed

Example:

ocrpdf.sh -r 90 file1.pdf file\ name\ 2.pdf

...will result in two new files, "file1.txt" and "file name 2.txt" in the current directory


```

#!/bin/bash

TESS_LANG=eng
rflag=
# first figure out what args we have
getopts 'r:' OPT;
shift $(($OPTIND - 1))
if [ $OPT == "r" ]
then
    rflag="-rotate $OPTARG";
fi

CURRENT_DIR=`pwd`
SCRIPT_NAME=`basename "$0" .sh`
TMP_DIR=${SCRIPT_NAME}-tmp
mkdir ${TMP_DIR}

for thisfile in "$@"
do
    NAME=`basename "${thisfile}" .pdf`
    cp "$thisfile" ${TMP_DIR}
    cd ${TMP_DIR}

    echo "Examining: ${thisfile}";
    pgs=`pdfinfo "${thisfile}" | grep Pages | awk '{print $2}'`
    echo "Found ${pgs} pages; converting...";
    # it's only fair, since we're suppressing it later...
    echo "Tesseract Open Source OCR Engine";
    for x in `seq 1 ${pgs}`
    do
        echo -en "  Page ${x}...";
        pdftoppm "$thisfile" -f $x -l $x -r 600 ocrbook;
        BASE=ocrbook-${x};
        convert ${BASE}.ppm ${rflag} ${BASE}.tif;
        tesseract ${BASE}.tif ${BASE} -l ${TESS_LANG} > /dev/null 2>&1;
        cat ${BASE}.txt >> "${NAME}.txt";
        echo "[pagebreak]" >> "${NAME}.txt";
        rm ocrbook*;
        echo "done";
    done;

    echo "Conversion complete";

    mv "${NAME}.txt" ${CURRENT_DIR}
    rm *
    cd ${CURRENT_DIR}
done

rmdir ${TMP_DIR}


```

---

### Post by tuxcantfly on 2010-04-17
I have made a ruby script which not only extracts text from the PDF using OCR (using the cuneiform software), but also embeds the extracted text back into the PDF. It also handles multi-page PDFs correctly.

See [http://github.com/gkovacs/pdfocr](http://github.com/gkovacs/pdfocr) for the script. The latest version can be obtained directly at [http://github.com/gkovacs/pdfocr/raw/master/pdfocr.rb](http://github.com/gkovacs/pdfocr/raw/master/pdfocr.rb)

I have also made a package for it at [https://launchpad.net/~gezakovacs/+archive/pdfocr](https://launchpad.net/~gezakovacs/+archive/pdfocr) and will be writing a howto for using it shortly.

Basically, it's just get the script, install the dependencies (ruby, cuneiform, and exactimage), and just run:

```
./pdfocr.rb -i input.pdf -o output.pdf
```

Or if using the version from the ppa, the dependencies should be installed automatically and all you need to do is:

```
pdfocr -i input.pdf -o output.pdf
```

---

### Post by tuxcantfly on 2010-04-18
> **tuxcantfly said:**
> I have made a ruby script which not only extracts text from the PDF using OCR (using the cuneiform software), but also embeds the extracted text back into the PDF. It also handles multi-page PDFs correctly.

See [http://github.com/gkovacs/pdfocr](http://github.com/gkovacs/pdfocr) for the script. The latest version can be obtained directly at [http://github.com/gkovacs/pdfocr/raw/master/pdfocr.rb](http://github.com/gkovacs/pdfocr/raw/master/pdfocr.rb)

I have also made a package for it at [https://launchpad.net/~gezakovacs/+archive/pdfocr](https://launchpad.net/~gezakovacs/+archive/pdfocr) and will be writing a howto for using it shortly.

Basically, it's just get the script, install the dependencies (ruby, cuneiform, and exactimage), and just run:

```
./pdfocr.rb -i input.pdf -o output.pdf
```

Or if using the version from the ppa, the dependencies should be installed automatically and all you need to do is:

```
pdfocr -i input.pdf -o output.pdf
```

My howto guide is located at [http://ubuntuforums.org/showthread.php?t=1456756](http://ubuntuforums.org/showthread.php?t=1456756)

---

### Post by gourneau on 2010-10-22
> **jfouse said:**
> Here's an updated version.

* Using khaeru's suggestion re: pdfinfo to do one page at a time, reducing overall drive space needed
* More explicitly looping over each of multiple named files
* Integrated an optional "-r <num>" param for rotating, if you know the pages need to be rotated.  This takes a degree measurement, and is passed directly to the -rotate param of convert.
* Cleanly handles filenames with spaces.
* Put the desired tesseract language in its own var up front so it's easily found and modified if needed

Example:

ocrpdf.sh -r 90 file1.pdf file\ name\ 2.pdf

...will result in two new files, "file1.txt" and "file name 2.txt" in the current directory




I modified your solution to work with Ubuntu 9.10 and pdftoppm 3.02  The problem I had was that pdftoppm pads the output .ppm with 5 zeros.  Mine will only work for pdfs less than 100 pages.

```

#!/bin/bash

TESS_LANG=eng
rflag=
# first figure out what args we have
getopts 'r:' OPT;
shift $(($OPTIND - 1))
if [ $OPT == "r" ]
then
    rflag="-rotate $OPTARG";
fi

CURRENT_DIR=`pwd`
SCRIPT_NAME=`basename "$0" .sh`
TMP_DIR=${SCRIPT_NAME}-tmp
mkdir ${TMP_DIR}

for thisfile in "$@"
do
    NAME=`basename "${thisfile}" .pdf`
    cp "$thisfile" ${TMP_DIR}
    cd ${TMP_DIR}

    echo "Examining: ${thisfile}";
    pgs=`pdfinfo "${thisfile}" | grep Pages | awk '{print $2}'`
    echo "Found ${pgs} pages; converting...";
    # it's only fair, since we're suppressing it later...
    echo "Tesseract Open Source OCR Engine";
    for x in `seq 1 ${pgs}`
    do
        echo -en "  Page ${x}...";
        pdftoppm -f $x -l $x -r 600 "$thisfile" ocrbook;
		if [ $x -gt 9 ]; then
        		BASE=ocrbook-0000${x};
		else 
        		BASE=ocrbook-00000${x};
		fi 
        convert ${BASE}.ppm ${rflag} ${BASE}.tif;
        tesseract ${BASE}.tif ${BASE} -l ${TESS_LANG} > /dev/null 2>&1;
        cat ${BASE}.txt >> "${NAME}.txt";
        echo "[pagebreak]" >> "${NAME}.txt";
        rm ocrbook*;
        echo "done";
    done;

    echo "Conversion complete";

    mv "${NAME}.txt" ${CURRENT_DIR}
    rm *
    cd ${CURRENT_DIR}
done

rmdir ${TMP_DIR}


```

---

### Post by nalin4linux77 on 2012-02-27
[B][SIZE=4][COLOR=Navy]Linux-intelligent-ocr-solution[/COLOR][/SIZE]

LIOS is a free and open source software for converting print in to text using either scanner or a camera. It can also produce text out of scanned images from other sources. Program is given total accessibility for visually impaired. LIOS is written in python and we release it under GPL3 license. LIOS will work with Debian based operating systems. LIOS is an effort from the easy-ocr development team. There are great many possibilities for this program. Feedback is the key to it. expecting your feedback. [EMAIL="nalin4linux77@gmail.com"]nalin4linux77@gmail.com[/EMAIL] and [EMAIL="sath.linux@gmail.com"]sath.linux@gmail.com[/EMAIL].
[SIZE=3][COLOR=Lime]HOW TO INSTALL[/COLOR][/SIZE]

Download deb file from here [http://linux-intelligent-ocr-solution.googlecode.com/](http://linux-intelligent-ocr-solution.googlecode.com/) download the latest deb package and install
What is new in LIOS-1.2
1 Cam-Scan,
2 Cam-Reader,
3 Scan-to-image-only,
4 Scan-to-images-repeatedly,
5 Introduction of py-sane, Glaid library make the program faster and efficient,
6 Multiple arguments are handled effectively,
7 Ocr a single Image,
8 Artha shortcut (alt+control+W),
9 Beta version of spell-checker,
10 Provision for submitting issues in the About Dialog.
Features
1 Single scan & Repeated Scanning,
2 Ocr Folder,
3 Ocr Pdf,
4 Ocr image only,
5 Cam-Scan and Cam-Reader,
6 Scan-for-image-only & repeatedly,
7 24 Language support (Given at the end),
8 Full GUI environment,
9 Selection of starting page number, page numbering mode and number of pages to scan,
10 Selection of Scan area, brightness, resolution and time between repeated scanning,
11 Full Auto Rotation,
12 Brightness optimizer,
13 Audio converter,
14 Easily Accessible Preferences Window,
15 5 OCR Engines (OCROPUS,CUNEIFORM,TESSERACT,GOCR,OCRAD),
16 Good text manipulation with Find, Go-To-Page, Go-To-Line, Append file, Punch File.
17 Display Preferences for Low vision,
18 Dictionary Support for English(Artha)
19 Beta version of spell-checker,
20 Provision for submitting issues,
21 And more features are in the preferences.[/B]:lolflag:
[B]
[SIZE=3][COLOR=Navy]How to start using LIOS.[/COLOR][/SIZE][/B]

1. Scanning.

In order to start new scan, first press ctrl+n and then press f9 for single scan or ctrl+f9 for repeated scanning. To set the scanning preferences press ctrl+p and set the starting page number, Mode of page numbering, double page mode if you intend to keep 2 pages at a time, rotation to select the way in which you want the program to rotate the images before conversion. In full automatic rotation mode, one can keep the book in 00 90 180 and 270 degree angle. In partial rotation mode program will scan once to find out the position of the book and then the rotation will be kept. In manual mode one should select the angle. partial and manual mode is faster than full auto rotation mode in ocr process. One can select the number of pages to be scanned at a stretch by setting number of pages in the case of repeated scanning. One can stop all scanning process by pressing ctrl f4.
2. Cam-scan.

one can now use Hovercam or a Webcam to produce text in LIOS. Adjustments with these devices can be made using LIOS-cam-preferences in edit menu. This feature will help to read books and other printed materials such as visiting cards currency and like and also it makes the ocr process very fast and accurate. Please be specific to use devices with auto focusing facility. remember that there is no autorotation in this utility.so for the same reason, support of a stand for the webcam will be highly appreciated.
3. Cam-reader.

is the utility which will give a continuous output as one moves the webcam. First it will create the image and then will produce the text and it will start reading. After the completion of reading, it will repeat the process automatically. In cam-scan, one has to take the photo and it will be converted in to text.
4. Ocr Image.

LIOS can convert image file to text which is in jpg, tif, png, pnm and bmp.
5. Ocr folder.

LIOS can convert scanned images from other sources. It can convert jpg, jpeg, tif, tiff png, pnm, formats. To convert the images in a folder, select scan from folder option from scan menu and then select the input folder.
6. Ocr Pdf file.

Select Ocr pdf from scan menu and then select the input file. It is recommended that one can use ocropus as engine more efficiently in pdf conversion.
7. scan for image only and scan for images only repeatedly.

Help one to scan only images and it will give the user opportunity to utilize different ocr engines conveniently. Also it avoids delay between each scan if one does not want to listen to the output. Images will be saved in LIOS or one can choose his own destination. Now conversion can be done using folder option.
8. Brightness checker.

To set a n exact value of brightness or threshold is the best way to ensure maximum efficiency out of ocr engines. To find out the best value, go to tools menu and select brightness checker. This utility will scan for 15 or 17 times to complete the process. After the process, number of words detected at different values will be shone in tabs. If you want to know the precise value only, shift tab and then tab to apply the value.
9. Audio conversion.

LIOS can convert the text opened in LIOS to wav files. To convert the text in to speech, go to tools menu and select audio converter.
10. Text Manipulation.

To go to page, press ctrl+g and then type the page number, and tab to OK. In the case of double page type only odd number, for example 1 in the case of 1-2 and 11 in the case of 11-12. One can go to any line by pressing ctrl+l and ctrl+f will help to find any word in the document.
11. Display preferences.

display preferences in the edit menu will help to set fond size, color , italic, bold and color of the background.
12. Engines.

There are 5 engines in LIOS.out of these only cuneiform can handle 24 languages, list given at the end. All other engines can handle only English. Cuneiform is good for speed and picture skipping ,ocropus is good for layout analysis and pdf conversion.
13. Artha.

In order to find out the meaning of English words, first select the word and then press alt+ctrl+w and tab to find the meaning. Caution for the first time one has to press alt+control+w twice so as to switch on artha
14. Spell checker.

A beta version of spell checker is added to the program.press ctrl f7 and all the misspelled words will appear and one can change them.
Cuneiform support Bulgarian, Croatian, Czech, Danish, Dutch, English, Estonian, French, German, Hungarian, Italian, Latvian, Lithuanian, Polish, Portuguese, Romanian, Russian, Russian-English bilingual, Serbian, Slovene, Spanish, Swedish, Turkish, and Ukrainian.
[SIZE=3][COLOR=Red]Disclaimer[/COLOR][/SIZE]

    Copyright (c) 2011-2012 LIOS Development Team 

    All rights reserved . Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met: 

    Redistributions of source code must retain the below copyright notice, 

    this list of conditions and the following disclaimer. 

    Redistributions in binary form must reproduce the below copyright notice, 

    this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution. 

    Neither the name of the nor the easyocr team names of its 

    contributors may be used to endorse or promote products derived from this software without specific prior written permission. 

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE." 

[SIZE=4][COLOR=Lime]FREE SOFTWARE FREE SOCIETY[/COLOR][/SIZE][SIZE=4]:guitar:[/SIZE]

---

