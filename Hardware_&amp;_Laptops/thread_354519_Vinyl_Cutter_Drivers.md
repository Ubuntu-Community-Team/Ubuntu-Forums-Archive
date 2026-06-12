---
title: "Vinyl Cutter Drivers"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by schizoman on 2007-02-06
I'm just beginning my search, but I'm wondering what it's going to take to run a vinyl cutter for vinyl signs under Ubuntu?  Are there any machines out there with linux software available?

---

### Post by brucewestfall on 2008-07-21
Sorry about an answer that is several months late, but something is better than none.

Quite a while ago, I used the info found at 
[http://www.3x6.nl/inkscape_hpgl/Linux%20inkscape%20save%20as%20HPGL%20file%20for%20pen%20cutting%20plotter%20extension.html](http://www.3x6.nl/inkscape_hpgl/Linux%20inkscape%20save%20as%20HPGL%20file%20for%20pen%20cutting%20plotter%20extension.html)

It took some tweaking, but it works.

With the newest version of Inkscape(0.46), the old print command is no
more, so what I have to do is paste what needs cut into a new file, size
the page to fit the thing I want to cut, then save the file as
'newplot.ps'

I then run the command
./graphtec.sh < newplot.ps

...which sends the postscript file to the script 'graphtec.sh'
I also have the plotter settings as rotated.

Here is the altered file I am currently using:
(I put this file and the the hpgl distiller in my home directory in a folder called 'hpgl'.  Make sure 'graphtec.sh' is set to be executable.)

[HTML]#!/bin/sh
#
# PRINT TO CUTTER
# ---------------
#
# A small shell utility that can be used as a front-end
#       to pstoedit and hpgl-distiller to allow your *nix
#       applications to print directly to the vinly cutter
#       so long as they generate valid Postscript or EPS output
#
# Written by Paul L Daniels
#
# http://pldaniels.com
# http://pldaniels.com/hpgl-distiller
#
# HOW TO USE THIS SCRIPT
# ----------------------
#
# (eg, Inkscape).
# Most *nix programs let you print to a program via a pipe
#       (like Inkscape used to do pre-0.46), what you do is tell the software
#       to print to this script, it's that simple.  The script
#       will then dump the Postscript data to /tmp, process it
#       filter it and then finally send the distilled HPGL to the
#       cutter/plotter.
#
#

# Which device has the cutter/plotter attached
#
CUTTER=/dev/ttyS0
stty 9600 cs8 -parenb -parodd crtscts -ixon -ixoff -F /dev/ttyS0

TMPDIR=/tmp
INF=$TMPDIR/cutter.$$.eps
OUTF=$TMPDIR/cutter.$$.tmp
HPGL=$TMPDIR/cutter.$$.hpgl
REMOVE_INF=0

# If we have a parameter for this script,
#       then it will be the filename of the file
#       we want to have converted (ie, we're not
#       reading from STDIN
#
if [ $# -eq 1 ]; then
       # Input data comes from a file.
#
       INF=$1
       else

       # Input is coming via a pipe to STDIN
#
       cat > $INF
       REMOVE_INF=1
fi

# Convert the Postscript/SVG/DXF/PDF to full HPGL/2
# This scale works for Roland and Graphtec plotters - the 2 I have
pstoedit -xscale 1.115 -yscale 1.115 -f plot-hpgl $INF $OUTF


# Strip out the innapropriate HPGL commands so as
#       not to confuse our plotter/cutter
#
hpgl-distiller -i $OUTF -o $HPGL

# Send the data to the cutter.
#
#     the next 2 commands strip out the commands PA0,0; and PG0;
#     which send the plotter back to the origin
sed -i 's/PA0,0;//' $HPGL
sed -i 's/PG0;//' $HPGL
cat $HPGL > $CUTTER

#translation of what needs sent to the terminal

# stty 9600 cs8 -parenb -parodd crtscts -ixon -ixoff -F /dev/ttyS0
# cat /home/bruce/Desktop/cutter.28665.hpgl > /dev/ttyS0
#    remove the # on the last 4 commands to
#    Clean up the temporary files generated - I like to keep them for a
while.
#    located at /tmp

#rm $OUTF $HPGL
#if [ $REMOVE_INF -eq 1 ]; then
#       rm $INF
#       fi

# END OF SCRIPT[/HTML]

---

