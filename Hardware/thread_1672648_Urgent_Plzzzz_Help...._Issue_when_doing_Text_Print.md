---
title: "Urgent Plzzzz Help.... Issue when doing Text Printing from Java to Canon iR1018"
date: 2011-01-21
forum: Hardware
---

### Post by rameshZSL on 2011-01-21
Hi,
When printing a text file through a Java program to a Cannon iR1018 and iR1020 the print job vainishes when it reaches the printer.
From the printer specification it says PCL is optional and UFR is standard for both the printers.
Could you please update ASAP what could be the root cause of this issue.
The same program works fine when I print to the Cannon iR1022 and iR1024 printer and I am getting the page printed with "HelloWorld" string. 
The issue when I print to the Cannon iR1018 & iR1020 is the page not getting printed though I can see the print job is spooled out from the workstation where the print is initiated. There are no expection been thrown.
 
JRE version : 1.6.0_13
Thanks.
 
Test Code attached below :
 
package com.bh.print.printer;
import java.awt.print.Book;
import java.awt.print.PageFormat;
import java.awt.print.PrinterJob;
import java.io.*;
import java.nio.ByteBuffer;
import java.nio.channels.FileChannel;
import javax.print.*;
import javax.print.attribute.AttributeSet;
import javax.print.attribute.HashAttributeSet;
import javax.print.attribute.HashPrintRequestAttributeSet;
import javax.print.attribute.PrintRequestAttributeSet;
import javax.print.attribute.standard.Copies;
import javax.print.attribute.standard.OrientationRequested;
import javax.print.attribute.standard.PrinterName;
import com.sun.pdfview.PDFFile;
public class PrintTest {
public static void main(String[] args) throws IOException {
// PrintTest pt = new PrintTest();
// pt.printPDF();
// we are going to print "printtest.txt" file which is inside working
// directory
// File file = new File("C:\\temp\\test.txt");
// File file = new File("D:\\BH.pdf");
// InputStream is = new BufferedInputStream(new FileInputStream(file));
String str = "HelloWorld";
 
byte[] originalContent = null;
originalContent = str.getBytes();
ByteArrayOutputStream out = new ByteArrayOutputStream();
out.write(originalContent);
out.flush();
out.close();
 
 
// Discover the default print service. If you call
// PrintServiceLookup.lookupPrintServices
// then it will return an array of print services available and you can
// choose a
// printer from them
//PrintService service [] = PrintServiceLookup.lookupDefaultPrintService();
PrintService service [] = null;
 
// Doc flavor specifies the output format of the file (Mime type + Char
// encoding)
// You can retrieve doc flavors supported by the printer, like this
// DocFlavor [] supportedFlavors = service.getSupportedDocFlavors();
DocFlavor docFlavor = DocFlavor.BYTE_ARRAY.AUTOSENSE;
// Find a particular service by name;
AttributeSet asset = new HashAttributeSet();
asset.add(new PrinterName("LEX02", null));
service = PrintServiceLookup.lookupPrintServices(null, asset);
 
// Create the print job
DocPrintJob job = service[0].createPrintJob();
// Create the Doc. You can pass set of attributes(type of
// PrintRequestAttributeSet) as the
// 3rd parameter specifying the page setup, orientation, no. of copies,
// etc instead of null.
Doc doc = new SimpleDoc(str.getBytes("cp1252"), docFlavor, null);
 
PrintRequestAttributeSet aset = new HashPrintRequestAttributeSet();
aset.add(new Copies(1));
 
// Order to print, (can pass attributes instead of null)
try {
job.print(doc, aset);
} catch (PrintException e) {
e.printStackTrace();
}
// DocPrintJob.print() is not guaranteed to be synchronous. So it's
// better to wait on completion
// of the print job before closing the stream. (See the link below)
System.out.println("Printing done....");
 
}

---

