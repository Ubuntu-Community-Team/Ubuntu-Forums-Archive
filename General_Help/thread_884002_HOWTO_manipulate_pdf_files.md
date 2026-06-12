---
title: "HOWTO: manipulate pdf files"
date: 2008-08-08
forum: General Help
---

### Post by bcrowell on 2008-08-08
**Get good performance when you click on a pdf link in firefox**
Change the file association in edit>preferences>applications so that pdf files are opened by xpdf. Evince is slower than xpdf, and adobe reader is slower than evince.

**Check whether the file has its fonts embedded**
```
pdffonts foo.pdf
```

**Extract certain pages from a pdf**
```
pdftk foo.pdf cat 7-8 output pages_7_and_8.pdf
```

**View and/or print large pdf files in which every page is a bitmap**
Evince performs so poorly on this type of file as to be unusable. Use xpdf for viewing instead.

My experience is that trying to print this type of file directly using lpr, evince, or xpdf doesn't work -- I get no output. I suspect this is a problem with my printer running out of memory. If this is a problem for you, try the following script, which will extract all the pages into individual jpg files, which you can open and print with gimp:
```

#!/usr/bin/perl

if (@ARGV<1) {
  die "usage:\n  pdf2jpegs foo.pdf ... defaults to 150 dots per inch\n  pdf2jpegs foo.pdf 300 ... some other resolution";
}

use strict;
use POSIX;

my $input_pdf = shift @ARGV; # first command-line argument
die "input file $input_pdf not found" unless  -e $input_pdf;

my $resolution = shift @ARGV;
unless ($resolution>0) {$resolution=150}
print "input file is $input_pdf, resolution $resolution\n";

# Remove drm:
my $temp1 = POSIX::tmpnam();
my $cmd = "gs -q  -dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=$temp1 $input_pdf -c '.setpdfwrite'";
do_system($cmd)==0 or die "error executing command $cmd, $!";

my $temp2 = POSIX::tmpnam();
my $cmd = "pdftk \"$temp1\" dump_data >$temp2";
print "counting pages...\n";
do_system($cmd)==0 or die "error executing command $cmd, $!";
open(F,"<$temp2") or die "error opening file $temp2 for input, $!";
my $data = '';
{
  local $/; # slurp all input
  $data = <F>;
}
close F;
$data =~ m/NumberOfPages\:\ (\d+)/ or die "no appropriate NumberOfPages line in file $temp2";
my $npages = $1;
unlink $temp2;
print "...$npages\n";

my $pgm_root = POSIX::tmpnam();
for (my $i=1; $i<=$npages; $i++) {
  print "Processing page $i...\n";
  my $cmd = "pdftoppm -f $i -l $i -r $resolution -gray \"$temp1\" $pgm_root";
  do_system($cmd)==0 or die "error executing command $cmd, $!";
  my $pgm = "$pgm_root-".(sprintf "%06d",$i).".pgm"; # comes out as pgm because we use -gray
  my $cmd = "convert $pgm \"$input_pdf-".(sprintf "%04d",$i).".jpg\"";
  do_system($cmd)==0 or die "error executing command $cmd, $!";
  unlink $pgm;
}
unlink($temp1);

sub do_system {
  my $cmd = shift;
  #print "$cmd\n";
  return system($cmd);
}
```

**Remove DRM (not encryption) from a pdf**
```
gs -q -dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=temp.pdf foo.pdf -c '.setpdfwrite' && mv temp.pdf foo.pdf
```

**Concatenate pdf files**
```
pdftk a.pdf b.pdf cat output c.pdf
```

**Extract bitmapped graphics from a pdf**
```
pdfimages foo.pdf foo
```

**Convert a pdf file to plain text**
```
pdftotext foo.pdf foo.txt
```

---

