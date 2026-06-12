---
title: "Printer problems 14.04.2 LTS Brother HL-2040 series"
date: 2015-07-07
forum: Hardware
---

### Post by birdy62 on 2015-07-07
Hi,
On Gnome Ubuntu 14.04.2 LTS 64bit .
Using the drivers installed as detected by the OS the printer prints blank pages and does not stop . I installed the Linux drivers from the Brother site, the printer starts up but does not print. CUPS PDF printer is installed and works fine. Below is a copy of the test print out file as per the [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) page. This is produced by the driver automatically installed by Ubuntu causing the printer to print continuous blank pages. The printer worked fine in 9.10, 12.10 and still works ok when attached to a Windows 8.1 machine.  

```
%-12345X@PJL
@PJL SET ECONOMODE=OFF
@PJL SET MEDIATYPE=REGULAR
%!PS-Adobe-3.0
%Produced by poppler pdftops version: 0.24.5 (http://poppler.freedesktop.org)
%%Creator: LibreOffice 4.2.8.2
%%LanguageLevel: 3
%%DocumentSuppliedResources: (atend)
%%For: (badger)
%%Title: (Untitled1)
%RBINumCopies: 1
%%Pages: (atend)
%%BoundingBox: (atend)
%%EndComments
%%BeginProlog
%%BeginResource: procset xpdf 3.00 0
%%Copyright: Copyright 1996-2011 Glyph & Cog, LLC
/xpdf 75 dict def xpdf begin
% PDF special state
/pdfDictSize 15 def
/pdfSetup {
  /setpagedevice where {
    pop 2 dict begin
      /Policies 1 dict dup begin /PageSize 6 def end def
      { /Duplex true def } if
    currentdict end setpagedevice
  } {
    pop
  } ifelse
} def
/pdfSetupPaper {
  2 array astore
  /setpagedevice where {
    pop 2 dict begin
      /PageSize exch def
      /ImagingBBox null def
    currentdict end setpagedevice
  } {
    pop
  } ifelse
} def
/pdfStartPage {
  pdfDictSize dict begin
  /pdfFillCS [] def
  /pdfFillXform {} def
  /pdfStrokeCS [] def
  /pdfStrokeXform {} def
  /pdfFill [0] def
  /pdfStroke [0] def
  /pdfFillOP false def
  /pdfStrokeOP false def
  /pdfOPM false def
  /pdfLastFill false def
  /pdfLastStroke false def
  /pdfTextMat [1 0 0 1 0 0] def
  /pdfFontSize 0 def
  /pdfCharSpacing 0 def
  /pdfTextRender 0 def
  /pdfPatternCS false def
  /pdfTextRise 0 def
  /pdfWordSpacing 0 def
  /pdfHorizScaling 1 def
  /pdfTextClipPath [] def
} def
/pdfEndPage { end } def
% PDF color state
/opm { dup /pdfOPM exch def
      /setoverprintmode where{pop setoverprintmode}{pop}ifelse  } def
/cs { /pdfFillXform exch def dup /pdfFillCS exch def
      setcolorspace } def
/CS { /pdfStrokeXform exch def dup /pdfStrokeCS exch def
      setcolorspace } def
/sc { pdfLastFill not { pdfFillCS setcolorspace } if
      dup /pdfFill exch def aload pop pdfFillXform setcolor
     /pdfLastFill true def /pdfLastStroke false def } def
/SC { pdfLastStroke not { pdfStrokeCS setcolorspace } if
      dup /pdfStroke exch def aload pop pdfStrokeXform setcolor
     /pdfLastStroke true def /pdfLastFill false def } def
/op { /pdfFillOP exch def
      pdfLastFill { pdfFillOP setoverprint } if } def
/OP { /pdfStrokeOP exch def
      pdfLastStroke { pdfStrokeOP setoverprint } if } def
/fCol {
  pdfLastFill not {
    pdfFillCS setcolorspace
    pdfFill aload pop pdfFillXform setcolor
    pdfFillOP setoverprint
    /pdfLastFill true def /pdfLastStroke false def
  } if
} def
/sCol {
  pdfLastStroke not {
    pdfStrokeCS setcolorspace
    pdfStroke aload pop pdfStrokeXform setcolor
    pdfStrokeOP setoverprint
    /pdfLastStroke true def /pdfLastFill false def
  } if
} def
% build a font
/pdfMakeFont {
  4 3 roll findfont
  4 2 roll matrix scale makefont
  dup length dict begin
    { 1 index /FID ne { def } { pop pop } ifelse } forall
    /Encoding exch def
    currentdict
  end
  definefont pop
} def
/pdfMakeFont16 {
  exch findfont
  dup length dict begin
    { 1 index /FID ne { def } { pop pop } ifelse } forall
    /WMode exch def
    currentdict
  end
  definefont pop
} def
/pdfMakeFont16L3 {
  1 index /CIDFont resourcestatus {
    pop pop 1 index /CIDFont findresource /CIDFontType known
  } {
    false
  } ifelse
  {
    0 eq { /Identity-H } { /Identity-V } ifelse
    exch 1 array astore composefont pop
  } {
    pdfMakeFont16
  } ifelse
} def
% graphics state operators
/q { gsave pdfDictSize dict begin } def
/Q {
  end grestore
  /pdfLastFill where {
    pop
    pdfLastFill {
      pdfFillOP setoverprint
    } {
      pdfStrokeOP setoverprint
    } ifelse
  } if
  /pdfOPM where {
    pop
    pdfOPM /setoverprintmode where{pop setoverprintmode}{pop}ifelse 
  } if
} def
/cm { concat } def
/d { setdash } def
/i { setflat } def
/j { setlinejoin } def
/J { setlinecap } def
/M { setmiterlimit } def
/w { setlinewidth } def
% path segment operators
/m { moveto } def
/l { lineto } def
/c { curveto } def
/re { 4 2 roll moveto 1 index 0 rlineto 0 exch rlineto
      neg 0 rlineto closepath } def
/h { closepath } def
% path painting operators
/S { sCol stroke } def
/Sf { fCol stroke } def
/f { fCol fill } def
/f* { fCol eofill } def
% clipping operators
/W { clip newpath } def
/W* { eoclip newpath } def
/Ws { strokepath clip newpath } def
% text state operators
/Tc { /pdfCharSpacing exch def } def
/Tf { dup /pdfFontSize exch def
      dup pdfHorizScaling mul exch matrix scale
      pdfTextMat matrix concatmatrix dup 4 0 put dup 5 0 put
      exch findfont exch makefont setfont } def
/Tr { /pdfTextRender exch def } def
/Tp { /pdfPatternCS exch def } def
/Ts { /pdfTextRise exch def } def
/Tw { /pdfWordSpacing exch def } def
/Tz { /pdfHorizScaling exch def } def
% text positioning operators
/Td { pdfTextMat transform moveto } def
/Tm { /pdfTextMat exch def } def
% text string operators
/xyshow where {
  pop
  /xyshow2 {
    dup length array
    0 2 2 index length 1 sub {
      2 index 1 index 2 copy get 3 1 roll 1 add get
      pdfTextMat dtransform
      4 2 roll 2 copy 6 5 roll put 1 add 3 1 roll dup 4 2 roll put
    } for
    exch pop
    xyshow
  } def
}{
  /xyshow2 {
    currentfont /FontType get 0 eq {
      0 2 3 index length 1 sub {
        currentpoint 4 index 3 index 2 getinterval show moveto
        2 copy get 2 index 3 2 roll 1 add get
        pdfTextMat dtransform rmoveto
      } for
    } {
      0 1 3 index length 1 sub {
        currentpoint 4 index 3 index 1 getinterval show moveto
        2 copy 2 mul get 2 index 3 2 roll 2 mul 1 add get
        pdfTextMat dtransform rmoveto
      } for
    } ifelse
    pop pop
  } def
} ifelse
/cshow where {
  pop
  /xycp {
    0 3 2 roll
    {
      pop pop currentpoint 3 2 roll
      1 string dup 0 4 3 roll put false charpath moveto
      2 copy get 2 index 2 index 1 add get
      pdfTextMat dtransform rmoveto
      2 add
    } exch cshow
    pop pop
  } def
}{
  /xycp {
    currentfont /FontType get 0 eq {
      0 2 3 index length 1 sub {
        currentpoint 4 index 3 index 2 getinterval false charpath moveto
        2 copy get 2 index 3 2 roll 1 add get
        pdfTextMat dtransform rmoveto
      } for
    } {
      0 1 3 index length 1 sub {
        currentpoint 4 index 3 index 1 getinterval false charpath moveto
        2 copy 2 mul get 2 index 3 2 roll 2 mul 1 add get
        pdfTextMat dtransform rmoveto
      } for
    } ifelse
    pop pop
  } def
} ifelse
/Tj {
  fCol
  0 pdfTextRise pdfTextMat dtransform rmoveto
  currentpoint 4 2 roll
  pdfTextRender 1 and 0 eq {
    2 copy xyshow2
  } if
  pdfTextRender 3 and dup 1 eq exch 2 eq or {
    3 index 3 index moveto
    2 copy
    currentfont /FontType get 3 eq { fCol } { sCol } ifelse
    xycp currentpoint stroke moveto
  } if
  pdfTextRender 4 and 0 ne {
    4 2 roll moveto xycp
    /pdfTextClipPath [ pdfTextClipPath aload pop
      {/moveto cvx}
      {/lineto cvx}
      {/curveto cvx}
      {/closepath cvx}
    pathforall ] def
    currentpoint newpath moveto
  } {
    pop pop pop pop
  } ifelse
  0 pdfTextRise neg pdfTextMat dtransform rmoveto
} def
/TJm { 0.001 mul pdfFontSize mul pdfHorizScaling mul neg 0
       pdfTextMat dtransform rmoveto } def
/TJmV { 0.001 mul pdfFontSize mul neg 0 exch
        pdfTextMat dtransform rmoveto } def
/Tclip { pdfTextClipPath cvx exec clip newpath
         /pdfTextClipPath [] def } def
/Tclip* { pdfTextClipPath cvx exec eoclip newpath
         /pdfTextClipPath [] def } def
% Level 2/3 image operators
/pdfImBuf 100 string def
/pdfImStr {
  2 copy exch length lt {
    2 copy get exch 1 add exch
  } {
    ()
  } ifelse
} def
/skipEOD {
  { currentfile pdfImBuf readline
    not { pop exit } if
    (%-EOD-) eq { exit } if } loop
} def
/pdfIm { image skipEOD } def
/pdfMask {
  /ReusableStreamDecode filter
  skipEOD
  /maskStream exch def
} def
/pdfMaskEnd { maskStream closefile } def
/pdfMaskInit {
  /maskArray exch def
  /maskIdx 0 def
} def
/pdfMaskSrc {
  maskIdx maskArray length lt {
    maskArray maskIdx get
    /maskIdx maskIdx 1 add def
  } {
    ()
  } ifelse
} def
/pdfImM { fCol imagemask skipEOD } def
/pr { 2 index 2 index 3 2 roll putinterval 4 add } def
/pdfImClip {
  gsave
  0 2 4 index length 1 sub {
    dup 4 index exch 2 copy
    get 5 index div put
    1 add 3 index exch 2 copy
    get 3 index div put
  } for
  pop pop rectclip
} def
/pdfImClipEnd { grestore } def
% shading operators
/colordelta {
  false 0 1 3 index length 1 sub {
    dup 4 index exch get 3 index 3 2 roll get sub abs 0.004 gt {
      pop true
    } if
  } for
  exch pop exch pop
} def
/funcCol { func n array astore } def
/funcSH {
  dup 0 eq {
    true
  } {
    dup 6 eq {
      false
    } {
      4 index 4 index funcCol dup
      6 index 4 index funcCol dup
      3 1 roll colordelta 3 1 roll
      5 index 5 index funcCol dup
      3 1 roll colordelta 3 1 roll
      6 index 8 index funcCol dup
      3 1 roll colordelta 3 1 roll
      colordelta or or or
    } ifelse
  } ifelse
  {
    1 add
    4 index 3 index add 0.5 mul exch 4 index 3 index add 0.5 mul exch
    6 index 6 index 4 index 4 index 4 index funcSH
    2 index 6 index 6 index 4 index 4 index funcSH
    6 index 2 index 4 index 6 index 4 index funcSH
    5 3 roll 3 2 roll funcSH pop pop
  } {
    pop 3 index 2 index add 0.5 mul 3 index  2 index add 0.5 mul
    funcCol sc
    dup 4 index exch mat transform m
    3 index 3 index mat transform l
    1 index 3 index mat transform l
    mat transform l pop pop h f*
  } ifelse
} def
/axialCol {
  dup 0 lt {
    pop t0
  } {
    dup 1 gt {
      pop t1
    } {
      dt mul t0 add
    } ifelse
  } ifelse
  func n array astore
} def
/axialSH {
  dup 0 eq {
    true
  } {
    dup 8 eq {
      false
    } {
      2 index axialCol 2 index axialCol colordelta
    } ifelse
  } ifelse
  {
    1 add 3 1 roll 2 copy add 0.5 mul
    dup 4 3 roll exch 4 index axialSH
    exch 3 2 roll axialSH
  } {
    pop 2 copy add 0.5 mul
    axialCol sc
    exch dup dx mul x0 add exch dy mul y0 add
    3 2 roll dup dx mul x0 add exch dy mul y0 add
    dx abs dy abs ge {
      2 copy yMin sub dy mul dx div add yMin m
      yMax sub dy mul dx div add yMax l
      2 copy yMax sub dy mul dx div add yMax l
      yMin sub dy mul dx div add yMin l
      h f*
    } {
      exch 2 copy xMin sub dx mul dy div add xMin exch m
      xMax sub dx mul dy div add xMax exch l
      exch 2 copy xMax sub dx mul dy div add xMax exch l
      xMin sub dx mul dy div add xMin exch l
      h f*
    } ifelse
  } ifelse
} def
/radialCol {
  dup t0 lt {
    pop t0
  } {
    dup t1 gt {
      pop t1
    } if
  } ifelse
  func n array astore
} def
/radialSH {
  dup 0 eq {
    true
  } {
    dup 8 eq {
      false
    } {
      2 index dt mul t0 add radialCol
      2 index dt mul t0 add radialCol colordelta
    } ifelse
  } ifelse
  {
    1 add 3 1 roll 2 copy add 0.5 mul
    dup 4 3 roll exch 4 index radialSH
    exch 3 2 roll radialSH
  } {
    pop 2 copy add 0.5 mul dt mul t0 add
    radialCol sc
    encl {
      exch dup dx mul x0 add exch dup dy mul y0 add exch dr mul r0 add
      0 360 arc h
      dup dx mul x0 add exch dup dy mul y0 add exch dr mul r0 add
      360 0 arcn h f
    } {
      2 copy
      dup dx mul x0 add exch dup dy mul y0 add exch dr mul r0 add
      a1 a2 arcn
      dup dx mul x0 add exch dup dy mul y0 add exch dr mul r0 add
      a2 a1 arcn h
      dup dx mul x0 add exch dup dy mul y0 add exch dr mul r0 add
      a1 a2 arc
      dup dx mul x0 add exch dup dy mul y0 add exch dr mul r0 add
      a2 a1 arc h f
    } ifelse
  } ifelse
} def
end
%%EndResource
/CIDInit /ProcSet findresource begin
10 dict begin
  begincmap
  /CMapType 1 def
  /CMapName /Identity-H def
  /CIDSystemInfo 3 dict dup begin
    /Registry (Adobe) def
    /Ordering (Identity) def
    /Supplement 0 def
  end def
  1 begincodespacerange
    <0000> <ffff>
  endcodespacerange
  0 usefont
  1 begincidrange
    <0000> <ffff> 0
  endcidrange
  endcmap
  currentdict CMapName exch /CMap defineresource pop
end
10 dict begin
  begincmap
  /CMapType 1 def
  /CMapName /Identity-V def
  /CIDSystemInfo 3 dict dup begin
    /Registry (Adobe) def
    /Ordering (Identity) def
    /Supplement 0 def
  end def
  /WMode 1 def
  1 begincodespacerange
    <0000> <ffff>
  endcodespacerange
  0 usefont
  1 begincidrange
    <0000> <ffff> 0
  endcidrange
  endcmap
  currentdict CMapName exch /CMap defineresource pop
end
end
%%EndProlog
%%BeginSetup
% Disable CTRL-D as an end-of-file marker...
userdict dup(\004)cvn{}put (\004\004)cvn{}put
[{
%%BeginFeature: *Resolution 600x600dpi
<</HWResolution[600 600]>>setpagedevice
%%EndFeature
} stopped cleartomark
[{
%%BeginFeature: *PageSize A4
<</PageSize[595 842]/ImagingBBox null>>setpagedevice
%%EndFeature
} stopped cleartomark
[{
%%BeginFeature: *Duplex None
<</Duplex false>>setpagedevice
%%EndFeature
} stopped cleartomark
% x y w h ESPrc - Clip to a rectangle.
userdict/ESPrc/rectclip where{pop/rectclip load}
{{newpath 4 2 roll moveto 1 index 0 rlineto 0 exch rlineto
neg 0 rlineto closepath clip newpath}bind}ifelse put
% x y w h ESPrf - Fill a rectangle.
userdict/ESPrf/rectfill where{pop/rectfill load}
{{gsave newpath 4 2 roll moveto 1 index 0 rlineto 0 exch rlineto
neg 0 rlineto closepath fill grestore}bind}ifelse put
% x y w h ESPrs - Stroke a rectangle.
userdict/ESPrs/rectstroke where{pop/rectstroke load}
{{gsave newpath 4 2 roll moveto 1 index 0 rlineto 0 exch rlineto
neg 0 rlineto closepath stroke grestore}bind}ifelse put
userdict/ESPwl{}bind put
xpdf begin
%%BeginResource: font BAAAAA+LiberationSerif
%!PS-TrueTypeFont-29810
10 dict begin
/FontName /BAAAAA+LiberationSerif def
/FontType 42 def
/FontMatrix [1 0 0 1 0 0] def
/FontBBox [0 -442 1217 1442] def
/PaintType 0 def
/Encoding 256 array
dup 0 /c00 put
dup 1 /c01 put
dup 2 /c02 put
dup 3 /c03 put
dup 4 /c04 put
dup 5 /c05 put
dup 6 /c06 put
dup 7 /c07 put
dup 8 /c08 put
dup 9 /c09 put
dup 10 /c0a put
dup 11 /c0b put
dup 12 /c0c put
dup 13 /c0d put
dup 14 /c0e put
dup 15 /c0f put
dup 16 /c10 put
dup 17 /c11 put
dup 18 /c12 put
dup 19 /c13 put
dup 20 /c14 put
dup 21 /c15 put
dup 22 /c16 put
dup 23 /c17 put
dup 24 /c18 put
dup 25 /c19 put
dup 26 /c1a put
dup 27 /c1b put
dup 28 /c1c put
dup 29 /c1d put
dup 30 /c1e put
dup 31 /c1f put
dup 32 /c20 put
dup 33 /c21 put
dup 34 /c22 put
dup 35 /c23 put
dup 36 /c24 put
dup 37 /c25 put
dup 38 /c26 put
dup 39 /c27 put
dup 40 /c28 put
dup 41 /c29 put
dup 42 /c2a put
dup 43 /c2b put
dup 44 /c2c put
dup 45 /c2d put
dup 46 /c2e put
dup 47 /c2f put
dup 48 /c30 put
dup 49 /c31 put
dup 50 /c32 put
dup 51 /c33 put
dup 52 /c34 put
dup 53 /c35 put
dup 54 /c36 put
dup 55 /c37 put
dup 56 /c38 put
dup 57 /c39 put
dup 58 /c3a put
dup 59 /c3b put
dup 60 /c3c put
dup 61 /c3d put
dup 62 /c3e put
dup 63 /c3f put
dup 64 /c40 put
dup 65 /c41 put
dup 66 /c42 put
dup 67 /c43 put
dup 68 /c44 put
dup 69 /c45 put
dup 70 /c46 put
dup 71 /c47 put
dup 72 /c48 put
dup 73 /c49 put
dup 74 /c4a put
dup 75 /c4b put
dup 76 /c4c put
dup 77 /c4d put
dup 78 /c4e put
dup 79 /c4f put
dup 80 /c50 put
dup 81 /c51 put
dup 82 /c52 put
dup 83 /c53 put
dup 84 /c54 put
dup 85 /c55 put
dup 86 /c56 put
dup 87 /c57 put
dup 88 /c58 put
dup 89 /c59 put
dup 90 /c5a put
dup 91 /c5b put
dup 92 /c5c put
dup 93 /c5d put
dup 94 /c5e put
dup 95 /c5f put
dup 96 /c60 put
dup 97 /c61 put
dup 98 /c62 put
dup 99 /c63 put
dup 100 /c64 put
dup 101 /c65 put
dup 102 /c66 put
dup 103 /c67 put
dup 104 /c68 put
dup 105 /c69 put
dup 106 /c6a put
dup 107 /c6b put
dup 108 /c6c put
dup 109 /c6d put
dup 110 /c6e put
dup 111 /c6f put
dup 112 /c70 put
dup 113 /c71 put
dup 114 /c72 put
dup 115 /c73 put
dup 116 /c74 put
dup 117 /c75 put
dup 118 /c76 put
dup 119 /c77 put
dup 120 /c78 put
dup 121 /c79 put
dup 122 /c7a put
dup 123 /c7b put
dup 124 /c7c put
dup 125 /c7d put
dup 126 /c7e put
dup 127 /c7f put
dup 128 /c80 put
dup 129 /c81 put
dup 130 /c82 put
dup 131 /c83 put
dup 132 /c84 put
dup 133 /c85 put
dup 134 /c86 put
dup 135 /c87 put
dup 136 /c88 put
dup 137 /c89 put
dup 138 /c8a put
dup 139 /c8b put
dup 140 /c8c put
dup 141 /c8d put
dup 142 /c8e put
dup 143 /c8f put
dup 144 /c90 put
dup 145 /c91 put
dup 146 /c92 put
dup 147 /c93 put
dup 148 /c94 put
dup 149 /c95 put
dup 150 /c96 put
dup 151 /c97 put
dup 152 /c98 put
dup 153 /c99 put
dup 154 /c9a put
dup 155 /c9b put
dup 156 /c9c put
dup 157 /c9d put
dup 158 /c9e put
dup 159 /c9f put
dup 160 /ca0 put
dup 161 /ca1 put
dup 162 /ca2 put
dup 163 /ca3 put
dup 164 /ca4 put
dup 165 /ca5 put
dup 166 /ca6 put
dup 167 /ca7 put
dup 168 /ca8 put
dup 169 /ca9 put
dup 170 /caa put
dup 171 /cab put
dup 172 /cac put
dup 173 /cad put
dup 174 /cae put
dup 175 /caf put
dup 176 /cb0 put
dup 177 /cb1 put
dup 178 /cb2 put
dup 179 /cb3 put
dup 180 /cb4 put
dup 181 /cb5 put
dup 182 /cb6 put
dup 183 /cb7 put
dup 184 /cb8 put
dup 185 /cb9 put
dup 186 /cba put
dup 187 /cbb put
dup 188 /cbc put
dup 189 /cbd put
dup 190 /cbe put
dup 191 /cbf put
dup 192 /cc0 put
dup 193 /cc1 put
dup 194 /cc2 put
dup 195 /cc3 put
dup 196 /cc4 put
dup 197 /cc5 put
dup 198 /cc6 put
dup 199 /cc7 put
dup 200 /cc8 put
dup 201 /cc9 put
dup 202 /cca put
dup 203 /ccb put
dup 204 /ccc put
dup 205 /ccd put
dup 206 /cce put
dup 207 /ccf put
dup 208 /cd0 put
dup 209 /cd1 put
dup 210 /cd2 put
dup 211 /cd3 put
dup 212 /cd4 put
dup 213 /cd5 put
dup 214 /cd6 put
dup 215 /cd7 put
dup 216 /cd8 put
dup 217 /cd9 put
dup 218 /cda put
dup 219 /cdb put
dup 220 /cdc put
dup 221 /cdd put
dup 222 /cde put
dup 223 /cdf put
dup 224 /ce0 put
dup 225 /ce1 put
dup 226 /ce2 put
dup 227 /ce3 put
dup 228 /ce4 put
dup 229 /ce5 put
dup 230 /ce6 put
dup 231 /ce7 put
dup 232 /ce8 put
dup 233 /ce9 put
dup 234 /cea put
dup 235 /ceb put
dup 236 /cec put
dup 237 /ced put
dup 238 /cee put
dup 239 /cef put
dup 240 /cf0 put
dup 241 /cf1 put
dup 242 /cf2 put
dup 243 /cf3 put
dup 244 /cf4 put
dup 245 /cf5 put
dup 246 /cf6 put
dup 247 /cf7 put
dup 248 /cf8 put
dup 249 /cf9 put
dup 250 /cfa put
dup 251 /cfb put
dup 252 /cfc put
dup 253 /cfd put
dup 254 /cfe put
dup 255 /cff put
readonly def
/CharStrings 256 dict dup begin
/.notdef 0 def
/c0c 12 def
/c0b 11 def
/c0a 10 def
/c09 9 def
/c08 8 def
/c07 7 def
/c06 6 def
/c05 5 def
/c04 4 def
/c03 3 def
/c02 2 def
/c01 1 def
end readonly def
/sfnts [
<000100000009008000030010637674203e4240fa0000009c000002166670676d
73d323b0000002b400000705676c79664e51725f000009bc00000eb468656164
327f37d10000187000000036686865610779fe53000018a800000024686d7478
28780285000018cc000000346c6f636115b4195a000019000000001c6d617870
048906c60000191c0000002070726570409b59c20000193c0000027400>
<058d00150048053d000f0070053d000f000000000000000000000000000003ac
001900000000ffec00000000ffec00000000ffec0000fe4cfffa000000000000
0000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000000
000000000000080000000000009800a600b4008d00d9005d0000000000000046
00500069007500d900000000000000000000000000c100d10069000000000050
005a00aa008a0000000000000000000000000000000000000000000000ac00b8
005a0000000000500060008f0099000000000000000000000000000000000000
000000000050009700b300c700d9000000000000000000000050006d007b008d
00b500d9013100c90000016f00f20108008100c500b800f20131004d00000000
00000000000000000000000000000000020e0000006600000000006600000000
00000000000002db009b028b004a02e40000009900660000022f021000c4009c
015e000001740046008d0000000000000046003c000000000000000000000000
000000000087007d00000053006800760087000000000000053dfcda0009fff3
008f007d004a00820041006c0000000000000000000000bc019f030a00000354
009f00a600c100000000002f00000000000000000748036a02b60202fd930000
009100670091006101d90000028d03410044051101b4000000>
<404559585554535251504f4e4d4c4b4a494847464544434241403f3e3d3c3b3a
393837363531302f2e2d2c28272625242322211f181411100f0e0d0b0a090807
060504030201002c4523466020b02660b004262348482d2c452346236120b026
61b004262348482d2c45234660b0206120b04660b004262348482d2c45234623
61b0206020b02661b02061b004262348482d2c45234660b0406120b06660b004
262348482d2c4523462361b0406020b02661b04061b004262348482d2c011020
3c003c2d2c20452320b0cd442320b8015a51582320b08d44235920b0ed515823
20b04d44235920b0042651582320b00d44235921212d2c20204518684420b001
602045b04676688a4560442d2c01b10b0a432343650a2d2c00b10a0b4323430b
2d2c00b0282370b101283e01b0282370b10228453ab10200080d2d2c2045b003
25456164b050515845441b2121592d2c49b00e23442d2c2045b0004360442d2c
01b00643b00743650a2d2c2069b04061b0008b20b12cc08a8cb8100062602b0c
642364615c58b00361592d2c8a03458a8a87b0112bb0292344b0297ae4182d2c
4565b02c234445b02b23442d2c4b525845441b2121592d2c4b515845441b2121
592d2c01b005251023208af500b0016023edec2d2c01b005251023208af500b0
016123edec2d2c01b0062510f500edec2d2c462346608a8a462320468a608a61
b8ff8062232010238ab10c0c8a70456020b0005058b00161b8ffba8b1bb0468c
59b0106068013a2d2c2045b0032546524bb013515b58b0022546206861b00325
b003253f2321381b2111592d2c2045b00325465058b0022546206861b00325b0
03253f2321381b2111592d2c00b00743b006430b2d2c21210c6423648bb84000
622d2c21b08051580c6423648bb82000621bb200402f2b59b002602d2c21b0c0
51580c6423648bb81555621bb200802f2b59b002602d2c0c6423648bb8400062
6023212d2c4b53588ab004254964234569b0408b61b08062b020616ab00e2344
2310b00ef61b21238a121120392f592d2c4b535820b0032549646920b00526b0
062549642361b08062b020616ab00e2344b0042610b00ef68a10b00e2344b00e
f6b00e2344b00eed1b8ab00426111220392320392f2f592d2c45234560234560
23456023766818b08062202d2cb0482b2d2c2045b0005458b040442045b04061
441b2121592d2c45b1302f4523456160b0016069442d2c4b5158b02f2370b014
23421b2121592d2c4b515820b0032545695358441b2121591b2121592d2c45b0
1443b0006063b0016069442d2cb02f45442d2c452320458a60442d2c45234560
442d2c4b235158b90033ffe0b134201bb3330034005944442d2cb0164358b003
26458a586466b01f601b64b020606620581b21b04059b001615923586559b029
23442310b029e01b2121212121592d2cb0024354584b53234b515a58381b2121
591b21212121592d2cb0164358b004254564b020606620581b21b04059b00161
23581b6559b0292344b00525b00825082058021b0359b0042510b005252046b0
042523423cb00425b0072508b0072510b006252046b00425b0016023423c2058
011b0059b0042510b00525b029e0b02920456544b0072510b00625b029e0b005
25b00825082058021b0359b00525b003254348b00425b0072508b00625b00325
b0016043481b2159212121212121212d2c02b00425202046b004252342b00525
08b003254548212121212d2c02b0032520b0042508b0022543482121212d2c45
2320451820b00050205823652359236820b040505821b04059235865598a6044
2d2c4b53234b515a5820458a60441b2121592d2c4b545820458a60441b212159
2d2c4b53234b515a58381b2121592d2cb000214b5458381b2121592d2cb00243
5458b0462b1b21212121592d2cb002435458b0472b1b212121592d2cb0024354
58b0482b1b21212121592d2cb002435458b0492b1b212121592d2c208a08234b
538a4b515a5823381b2121592d2c00b0022549b000535820b04038111b21592d
2c014623466023466123201020468a61b8ff80628ab140408a704560683a2d2c
208a2349648a2353583c1b21592d2c4b52587d1b7a592d2cb012004b014b5442
2d2cb1020042b123018851b1400188535a58b910000020885458b20201024360
4259b12401885158b920000040885458b2020202436042b12401885458b20220
02436042004b014b5258b2020802436042591bb940000080885458b202040243
604259b94000008063b80100885458b202080243604259b94000010063b80200
885458b202100243604259b94000020063b80400885458b20240024360425959
5959592d2c451868234b51582320452064b04050587c59688a6059442d2cb000
16b00225b0022501b001233e00b002233eb10102060cb00a236542b00b234201
b001233f00b002233fb10102060cb006236542b0072342b00116012d2c7a8a10
4523f5182d00000000>
<0002004400000264055500030007002eb101002f3cb2070408ed32b10605dc3c
b2030208ed3200b103002f3cb2050408ed32b2070609fc3cb2010208ed323311
211125211121440220fe240198fe680555faab4404cd000000>
<00010025000004c1053d001701f140ff050d150d250d030a081a0802090f1901
fe0f194f195f197f198f19bf19df19ff1908f019018f199f19cf19037019010f
191f194f1903cf19df19ef1903b019019f19018019011f192f195f1903001901
ce6f19af19bf19ef19045019010f192f193f1903ff1901d01901bf1901a01901
3f194f197f19032019017f199f19bf19cf19ff19056019014f19013019010f19
019def1901d019012f196f197f19af1904101901bf19cf19ef19ff19049019a0
19027f19016019010f193f1902e019013f195f197f198f19bf19052019010f19
016bf01901cf1901a019018f19017019010f191f194f1903f01901cf1901b019
015f196f198f199f1904301940190240871f1901001901df19018019b019025f
190100193019023bff1901e01901cf1901b019014f195f198f1903301901b019
e019f019038f19017019015f190100192019301903f01901df1901c019019f19
0170198019021f192f193f1903001901500c800cb00cc00c040c025f098f09bf
09cf090409155a020d00090109091403600a0315025f0012003fed323fed3233
2f5d33012ffdcc5d10cc5d5d5d5d5d5d5d5d71717171717272727272725e5d5d
5d5d717171717171717272727272725e5d5d5d5d7171717171727272725e5d5d
5d5d5d7171717171717272725e5d5d5d5d5d5d71717171725e5d31305e5d5d21
3537112322060f012311211123272e032b01111715013bd53383b2251b43049c
441b12475e6f3a31d5351b04970c08d1013bfec5d104060503fb6b1b3500000000>
<00020050ffec034603c5001f002a0074402d8914019813010b138b1302161b26
1b020918191829189918040826481f0b0b1f2c002c013e802ca02cf02c032cb8
ffc0b3434a482cb8ffc040172a2e482501488816011600502525062050191006
511116003fed3fed12392fed012f5ded322b2b715e5d10ce322f10ed31305e5d
5d5d5d5d0115141e0233323e0237150e0323222e0235343633321e021d010122
0e021521342e020104153f725d1e42423e1a17414e582d75a1642ccebf4b8362
39fe97385135190192112b4801d9124986673d05080a06380f1b160d407eba79
f6f2285e9e7652019c2f567b4c4c7b562f00000000>
<00010054ffec02d303c5003500a140244a328a32027c158c15023a164a167a16
8a1604053315332533033c1a4c1a7c1a8c1a0402b8ffd84017090d481e18090c
48254010154825251346003720370137b8ffc040301e21484f375f37af37032d
461c0b0b1c132d052a5021342644260226262110105005340b440ba40b03200b
010b0b0516003f332f5d5d10ed3f332f5d10ed123939012f332f10ed5d2b7110
deed332f2b31302b2b5d005d5d5d5d01140e0223222e02273533171e01333236
35342e0635343e02333216171523272e0123220615141e0602d32754855e2f5b
4e3a0d2d311f62425d652a44575b57442a2e53734544823c2f2a1a5a3351552a
45585c58452a01083f694b290b0f1005e7831c28515532412c1d1e263c5a4340
644423130ccd6d171850442e3b291e2029405c0000>
<00010014ffec022d04810019005740390238081148040601af1b01c01b013f1b
4f1b020a0e47035014601402141407000310032003030803040c500940090e48
09070b0f1511510016003fed333f33ce2bed32012f5e5d33332f5d10ed325d5d
7231305d2b052226351123353f01331533152311141633323637150e03014e60
5f7b7d653fd7d73b3025491f0f313b4214726702932d27d5d554fd7f41420a06
410a140f0a00000000>
<00020021fe4c03b003c50021003000904065692f792f02061d01841194110206
1101840b940b02030b01080601010922480e3240320100328032023940320150
3270329032d032f0320570329032d032034f32012b16041c47002110212021d0
21040821211c501e1b2e5013162a27510409100050030f003fed3f33ed323fed
3fed32012f5e5ded3232325d5d71725e5d7210deed31305e5d5e5d5d5d5d5d5d
13273521173e0333321e0215140e02232226271e031d01171521353701342e02
23220607111e01333236986b0108021539424a26588c623334689d6933713301
030101a4fe4077026422415e3b306d262a663384780366192d37121d150c3e7b
b57673b983460b0b0c1f211c09fe182f2f18034e66905b2a1110fd110809db0000>
<000100290000029803c50018006bb3040a0102b8ffd8402f090f48131f016f01
7f010301010947000e100e200ec00ed00ee00e06080e1f1a5f1a02401a015613
66130213031802b8ffc04010090c48020218100f50120f090e500c15003fed32
3fed3f332f2b10c9335d0171722f5e5ded322f5d3231302b5d01152327220e02
0711171521353711273521173e033302982b3a1c40403b16a1fe427777011209
17505d5d2403c5fe6e080d120afd42192d2d190320192d7513312c1e00>
<0002002b00000212054c0013001d009c4053004a0b0a9b0aab0a03eb0afb0a02
840a010a19470b142b14024b145b149b14fb14040b142b143b14ab14bb14eb14
06101440393d48141f041f141f0239f41f01901f0102501fa01fb01fc01f0490
1fa01f021fb8ffc0b32d30481fb8ffc0b3181b481fb8ffc040100d104805530f
041a501d0f1419501715003fed323fed3fed012b2b2b5d715f72725e5d10dc2b
5e5d7172fdd45d5d71ed313001140e0223222e0235343e0233321e0203171521
353711273521017b111e281616271e11111e271616281e110aa1fe19a085012b
04df16271e11111e271616281e11111e28fb51192d2d190320192d0000>
<0001002f000003e103c5002300b6b90008ffe0402a091048040801080f10090c
480f10470b0beb0b02160b25a4250104251425c425e4250439a425f4250225b8
ffc040182b30482b2501142501c02501025025017025802590250325b8ffc0b3
1f224825b8ffc0402d131648001a47801fc01f02001f101f201fc01fd01fe01f
06081f2050230f1a100b1f500e1d1519000014520510003fed3311333f33ed32
32323fed012f5e5d71ed322b2b5d715f7172722b725e5d7110dc5e5ded322b31
305e5d2b013e0333321e021511171521353711342623220e0207111715213537
1127352101441c4d545424365a412572fe6b7d51551c3e3c35127ffe6a717101
0c036010241e131e426a4bfd96192d2d190258535f06080b04fd13192d2d1903
20192d0000>
<00030058fe4603d9041b003400470059018d401779450156316631023120080c
4848315831683188310431b8ffc04009080c480218080b4832b8ffd8400e0810
482428080c482718080b480db8ffe04056080f481620080c481f38080d482028
081048074722322e062304005548252240191d482540191d482225222518870e
010e4635401a1d4835354b482b0001bb0001040014000209005b545b01405b01
345b01205b015bb8ffc04012596048805b01745b01605b01b45bc45b025bb8ff
c0401b4d5448a05b01045b013f045b845ba45b03a45bc45bd45be45b045bb8ff
c0b34148485bb8ffc0b3353d485bb8ffc0b32b2f485bb8ffc040131e2148405b
01345b01205b0102205b305b025bb8ffc0402e0f1a48393e491d301801180623
322f042a0350481d380b0f481f482f4803a00b01480b480b4350502a10435013
1c003fed3fed1239392f2f5d5d10cd3210ed111739012f5d33ed322b5d5f7171
712b2b2b2b71725e5d5d2b5d7171712b7272727210de5e5d5d71ed332f2bed5d
1239392f2f2b2b10ed12173910ed31302b2b2b2b2b2b2b002b2b5d012b5d5d01
140623222627071e013321321615140e0223222e0235343e02372e0335372635
343e0233321e02173717071e0103342623210e0315141e0233323e0201323635
342e0223220e0215141e020366c2b629531c3f034836011698933577c08c6b96
5e2a192d3e24122f2a1c9e9e34618e5a1c3a332609dd238b2221294647fe9415
23190e1739624a5a835629feb36d5b152f4c36374d311616304c0283a2a60906
83111e8474417d613b233e5230213b37341a061b2a3722b24ad94f7951290607
09036f2b902673fcba3940122f343519243b2a18233f5602397d7f3f5d3c1e1e
3c5d3f3f5f3f1f0000>
<0001003f000002aa05a2002101af400d09061906290603080b2301fd23b8ffc0
405ef8fb488b2301342344236423038423d423e423f423047023011423442354
23642304542364237423b423e423f423060b231b2302ccf02301c423d423e423
038b230134236423742303a423d423e423f42304542364237423e423f4230523
b8ffc0400ab0b3480b231b23029c23b8ffc0400c989b489b2301742384230223
b8ffc04031898d48ab2301542364238423031b2301042301f42301bb23016423
74238423031b232b23020423016b6423842394230323b8ffc040906568484b23
01042301f42301ab23bb23029423012b235b23020423142302ab23bb23cb2303
04231423442354237423053afb2301b423d42302a02301242334234423742384
239423061023010200230120233023502380239023b023e023f0230810232023
8023c02304180d0d1c470300211021202180210408211c21501f15001a500319
0f1250095f0e010e0e0901003f332f5d10ed3f33ed323fed32012f5e5d32ed32
2f325d71725f72727272725e5d5d717171717172722b725e5d5d5d5d5d717171
712b72722b5e5d2b5d71727272725e5d5d71717172722b5e5d31305e5d132335
3735343e02333216171523272e0123220e021d01331523111715213537e1a2a2
2b5175492d461c312d10261c232c1a0afafacbfe048b03583127426aa16d380b
08cd7b0a0b1f4164469c54fcf6212d2d2100000000>
<0001002900000210058d00090087402805472b00010b00013a5b006b007b009b
00041b005b00bb00cb00047b009b00ab0003000bc40b010bb8ffc0b33f46480b
b8ffc0401c383b48900b0102000b100b500ba00bb00bc00b06900ba00bf00b03
0bb8ffc0b32d30480bb8ffc0400c0d1048065009000005500315003fed323fed
012b2b5d715f722b2b7210dc5d71725e5d71ed31302517152135371127352101
6fa1fe19a0a0014646192d2d190502182d00000000>
<00010000000111eb81700d3c5f0f3cf5001f080000000000ce8add0100000000
000000000000fe4604c105a200000008000200000000000000>
<000100000721fe45005700000000000000000001000000000000000000000000
0000000d00>
<02ec004404e30025038d0050031d005402390014020000000400002102aa0029
0239002b0400002f0400005802aa003f0239002900>
<0000002c014c01c6026002b402b4034403a2042004b205f60700075a00>
<00010000000d005a00030000000000020010002f005a0000040b06390003000200>
<b10960be01070001003f0107000100bf0104405901e0fd01cffd0120fd017ffb
0150fb0180f290f202f1f0291faff0bff0024fef5fefafef0330ef010fef0108
00ed10ed50ed60ed70eda0ed060a0fec010c00eb0111e3e0381fdf33dd55de33
dc5500dd013c50dd80ddb0dd03b8ffc0405add080b46dd010355dc03161f10c0
20c030c070c080c0d0c0e0c0f0c00880be90be02bdbc2f1f0fbc1fbc021fb34f
b37fb30360a8010fa81fa802509b609b02909c010f9c1f9c2f9c039a992e1f99
471e1f9796271fe096f09602b8ffc04035960d11465f95017f928f9202708680
869086038085908502af76bf76027350291f6f6e2b1f6e472a1f193318550733
03550603ff1fb8ffc0404462252846605f401f5f50291f5b5a301f5a47291f13
33125505010355043303550f031f033f034f036f038f03bf03070852501e1f51
501e1fe050f050020f4f1f4f2f4f03b8ffe040614b212846604a704a804a0349
46291f4847381f0f471f472f47cf47df47ef47065f47019f47019f46af46bf46
034046292f4640461e21461c481b551633155510330f5502010055013300552f
0fff0f020f0f5f0f7f0f030f003f00028016010501b80190b154532b2b4bb807
ff524bb008505bb00188b02553b00188b040515ab00688b000555a5b58b10101
8e59858d8d00421d4bb0325358b0601d594bb0645358b0401d594bb0805358b0
101db1160042597373742b2b2b2b2b012b2b737374752b2b73002b75742b2b5e
732b2b2b012b2b002b2b2b2b2b2b012b2b002b73017373007373012b732b2b2b
737300737373017300732b017373002b2b2b735e732b2b012b5e735e73005e73
5e73737301732b7300737373737301737373185e00>
] def
FontName currentdict end definefont pop
%%EndResource
/F8_0 /BAAAAA+LiberationSerif 1 1
[ /c00/c01/c02/c03/c04/c05/c06/c07
  /c08/c09/c0a/c0b/c0c/c0d/c0e/c0f
  /c10/c11/c12/c13/c14/c15/c16/c17
  /c18/c19/c1a/c1b/c1c/c1d/c1e/c1f
  /c20/c21/c22/c23/c24/c25/c26/c27
  /c28/c29/c2a/c2b/c2c/c2d/c2e/c2f
  /c30/c31/c32/c33/c34/c35/c36/c37
  /c38/c39/c3a/c3b/c3c/c3d/c3e/c3f
  /c40/c41/c42/c43/c44/c45/c46/c47
  /c48/c49/c4a/c4b/c4c/c4d/c4e/c4f
  /c50/c51/c52/c53/c54/c55/c56/c57
  /c58/c59/c5a/c5b/c5c/c5d/c5e/c5f
  /c60/c61/c62/c63/c64/c65/c66/c67
  /c68/c69/c6a/c6b/c6c/c6d/c6e/c6f
  /c70/c71/c72/c73/c74/c75/c76/c77
  /c78/c79/c7a/c7b/c7c/c7d/c7e/c7f
  /c80/c81/c82/c83/c84/c85/c86/c87
  /c88/c89/c8a/c8b/c8c/c8d/c8e/c8f
  /c90/c91/c92/c93/c94/c95/c96/c97
  /c98/c99/c9a/c9b/c9c/c9d/c9e/c9f
  /ca0/ca1/ca2/ca3/ca4/ca5/ca6/ca7
  /ca8/ca9/caa/cab/cac/cad/cae/caf
  /cb0/cb1/cb2/cb3/cb4/cb5/cb6/cb7
  /cb8/cb9/cba/cbb/cbc/cbd/cbe/cbf
  /cc0/cc1/cc2/cc3/cc4/cc5/cc6/cc7
  /cc8/cc9/cca/ccb/ccc/ccd/cce/ccf
  /cd0/cd1/cd2/cd3/cd4/cd5/cd6/cd7
  /cd8/cd9/cda/cdb/cdc/cdd/cde/cdf
  /ce0/ce1/ce2/ce3/ce4/ce5/ce6/ce7
  /ce8/ce9/cea/ceb/cec/ced/cee/cef
  /cf0/cf1/cf2/cf3/cf4/cf5/cf6/cf7
  /cf8/cf9/cfa/cfb/cfc/cfd/cfe/cff]
pdfMakeFont
false pdfSetup
[{
%%BeginFeature: *Resolution 600x600dpi
<</HWResolution[600 600]>>setpagedevice
%%EndFeature
} stopped cleartomark
[{
%%BeginFeature: *PageSize A4
<</PageSize[595 842]/ImagingBBox null>>setpagedevice
%%EndFeature
} stopped cleartomark
[{
%%BeginFeature: *Duplex None
<</Duplex false>>setpagedevice
%%EndFeature
} stopped cleartomark
%%EndSetup
%%Page: 1 1
%%PageBoundingBox: 0 0 595 842
%%BeginPageSetup
%%EndPageSetup
595 842 pdfSetupPaper
pdfStartPage
0 0 595 842 re W
[] 0 d
1 i
0 j
0 J
10 M
1 w
/DeviceGray {} cs
[0] sc
/DeviceGray {} CS
[0] SC
false op
false OP
{} settransfer
q
0.12 w
q
/DeviceRGB {} cs
[0 0 0] sc
[1 0 0 1 0 0] Tm
0 0 Td
56.8 774.1 Td
/F8_0 12 Tf
(\001)
[7.32
0] Tj
70 TJm
(\002)
[5.316
0] Tj
3 TJm
(\003\004)
[4.668
0
3.324
0] Tj
-2 TJm
(\005\006\007)
[3
0
6
0
3.996
0] Tj
3 TJm
(\010)
[3.324
0] Tj
-2 TJm
(\011\004)
[6
0
3.324
0] Tj
-2 TJm
(\010)
[3.324
0] Tj
-2 TJm
(\011\012\005\013)
[6
0
6
0
3
0
3.996
0] Tj
3 TJm
(\010)
[3.324
0] Tj
-2 TJm
(\014)
[3.324
0] Tj
-2 TJm
(\002)
[5.316
0] Tj
Q
Q
showpage
%%PageTrailer
pdfEndPage
%%Trailer
end
%%DocumentSuppliedResources:
%%+ font BAAAAA+LiberationSerif
%%Pages: 1
%%BoundingBox: 0 0 595 842
%%EOF
%-12345X@PJL RESET
```

---

