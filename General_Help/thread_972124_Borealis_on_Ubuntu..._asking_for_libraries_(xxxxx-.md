---
title: "Borealis on Ubuntu... asking for libraries (xxxxx-lt-Stockdist) that it can't find..."
date: 2008-11-05
forum: General Help
---

### Post by mineiro_rdf on 2008-11-05
Hi,

I am facing a problem that is unusual, because first of all the application that I am trying to run it's called Borealis, and it is for distributed stream processing.

[http://www.cs.brown.edu/research/borealis/public/install/install.borealis.html](http://www.cs.brown.edu/research/borealis/public/install/install.borealis.html)

Then I got it installed on Ubuntu...
And I could run a example of Map box in a single node.

The problem comes when I try to run in more than one node...
So I've deployed two Map boxes each one in different ports, in the same host (127.0.0.1:15000, and 127.0.0.1:17000).

So in order to do this example I've done the following:
I've written this 2 Map Boxes in the stockdist.xml file:

--------------------------stockdist.xml-------------------------------
<?xml version="1.0"?>
<!DOCTYPE borealis SYSTEM "/home/rodrigo/software/borealis/src/src/borealis.dtd">

<!-- Borealis query diagram for:  mytestdist.cc -->

<borealis>

	<input stream="Stock_USD" schema="StockType_USD" />
	<output stream="Stock_BR" schema="StockType_BR" />

	<schema name="StockType_USD">
	    <field name="symbol"      type="string" size="4" />
	    <field name="time"        type="int"             />
	    <field name="price_usd"   type="double"          />
	</schema>

<!--	<schema name="StockType_CAD">
	    <field name="symbol"      type="string" size="4" />
	    <field name="time"        type="int"             />
	    <field name="price_cad"   type="double"          />
	</schema> -->

	<schema name="StockType_BR">
	    <field name="symbol"      type="string" size="4" />
	    <field name="time"        type="int"             />
	    <field name="price_br"   type="double"          />
	</schema>

<query name="USQuoteToCanadian">
	<box name="USQuoteToCanadi" type="map">
	    <in stream="Stock_USD" />
	    <out stream="Stock_CAD" />
	    <parameter name="expression.0"        value="symbol"         />
	    <parameter name="output-field-name.0" value="symbol"         />
	    <parameter name="expression.1"        value="time"           />
	    <parameter name="output-field-name.1" value="time"           />
	    <parameter name="expression.2"        value="price_usd/0.75" />
	    <parameter name="output-field-name.2" value="price_cad"      />
	</box>
</query>
<query name="CADQuoteToBrazilian">
	<box name="CADQuoteToBrazili" type="map">
	    <in stream="Stock_CAD" />
	    <out stream="Stock_BR" />
	    <parameter name="expression.0"        value="symbol"         />
	    <parameter name="output-field-name.0" value="symbol"         />
	    <parameter name="expression.1"        value="time"           />
	    <parameter name="output-field-name.1" value="time"           />
	    <parameter name="expression.2"        value="price_cad/2.50" />
	    <parameter name="output-field-name.2" value="price_br"      />
	</box>
</query>

</borealis>


and in the stockdist-delploy.xml the nodes that it should be deployed
(127.0.0.1:15000, and 127.0.0.1:17000):

--------------------------stockdist-deploy.xml-------------------------------
<?xml version="1.0"?>
<!DOCTYPE borealis SYSTEM "/home/rodrigo/software/borealis/src/src/borealis.dtd">

<deploy>
    <publish    stream="Stock_USD" node="127.0.0.1:15000"/>
    <subscribe  stream="Stock_BR" node="127.0.0.1:20000"/>

    <node   endpoint="127.0.0.1:15000"  query="USQuoteToCanadian" />
    <node   endpoint="127.0.0.1:17000"  query="CADQuoteToBrazilian" />

</deploy>


Then I used a tool from borealis which generates the header file and the cpp file
from those xml files (so far, so good, it doesn't give any error or even warning):
Here are those files (StockdistMarshal.h and StockdistMarshal.cpp):

//////StockdistMarshal.h
#ifndef  STOCKDISTMARSHAL_H
#define  STOCKDISTMARSHAL_H

#include  "MedusaClient.h"
#include  "TupleHeader.h"

////////////////////////////////////////////////////////////////////////////////
//
// Generated Martialing code for the Stockdist program.
//..............................................................................


using namespace Borealis;

class StockdistMarshal
{
  public:

    StockdistMarshal() {};
   ~StockdistMarshal() {};

    /// Activate the front-end and subscribe to streams.
    /// Returns 0 if okay; else an error occured.
    ///
    int32  open();


    /// Connect to inputs and subscribe to streams only.
    /// Similar to open() but does not load the query.
    ///
    void  openInputOutput();


    /// Run the client event loop.
    /// This does not return unless terminated or on an exception.
    ///
    void  runClient();


    /// Terminate the client event loop.
    ///
    void  terminateClient();


    /// Copy a string value to a fixed length array and zero fill.
    ///
    static void  setStringField(string  value,
                                  char  field[],
                                uint32  length)
                          throw(AuroraException);


    /// Get the timestamp for a tuple.
    ///
    static timeval   getTimeValue(uint8  *tuple)
    {
       return(*((timeval *)(tuple - HEADER_SIZE)));
    }


  public:

    struct StockType_USD
    {
        char    symbol[ 4 ];
        int32    time;
        double    price_usd;
    } __attribute__((__packed__));

    struct  Stock_Usd : public TupleHeader
    {
        StockType_USD   _data;
    } __attribute__((__packed__));

    /// The sentStock_Usd  method must be defined by the application.
    /// It is called after sendStock_Usd is done and a pause.
    ///
    void  sentStock_Usd();

    /// Enque a Stock_Usd for input.
    ///
    void  batchStock_Usd(Stock_Usd  *tuple);

    /// Send enqued Stock_Usd inputs.
    ///
    void  sendStock_Usd(uint32  sleep);

  private:

    /// Connect the Stock_Usd input stream.
    ///
    void  connectStock_Usd();

    ///  Resume here.  Extend with a user callback.
    void  delayStock_Usd();

  private:

    /// Handler to dispatch tuples received.
    ///
    static Status outputHandler(ptr<StreamEvent> event);


  public:

    struct StockType_BR
    {
        char    symbol[ 4 ];
        int32    time;
        double    price_br;
    } __attribute__((__packed__));

    /// The receivedStock_Br method must be defined by the application.
    /// It is called after a(n) StockType_BR is received.
    ///
    static void  receivedStock_Br(StockType_BR  *tuple);

  private:

    /// Subscribe to the Stock_Br output stream.
    ///
    void  subscribeStock_Br();

    /// Handler to receive tuples from the Stock_Br stream.
    ///
    static Status  Stock_BrHandler(ptr<StreamEvent>  event);

  private:

    /// Launch the Borealis front-end.
    ///
    static int32  launchDiagram(string  xml);  // Path of an initial xml file.

    /// Client connections to Borealis nodes.
    ///
    MedusaClient      *_client;


    /// Event state for input streams.
    /// These are declared with a smart pointer as fast_post_event requires it.
    ///
    ptr<StreamEvent>   _eventStock_Usd;
};

#endif                         // STOCKDISTMARSHAL_H


The other file StockdistMarshal.cpp:
/////////////////////////////////////StockdistMarshal.cpp///////////////////////////////////////////////
#include  "StockdistMarshal.h"
#include  "util.h"

#define STOCKDIST_XML     "stockdist.xml stockdist-deploy.xml"
#define MAX_BUFFER      640000000

#define STOCKDIST_ENDPOINT     "138.100.12.92:25000"

#define STOCK_USD  "stock_usd"
#define STOCK_BR  "stock_br"

////////////////////////////////////////////////////////////////////////////////
//
// Generated marshaling code for the Stockdist program.
//..............................................................................


////////////////////////////////////////////////////////////////////////////////
//
//  Subscribe to input and output streams.
//
int32  StockdistMarshal::open()
{
    int32   status;
//..............................................................................


    // Open a client to send and receive data.
    //
    _client = new MedusaClient(InetAddress());

    // Subscribe to outputs.
    //
    subscribeStock_Br();

    //  Launch the front-end with the xml file.
    //  Creates a client that communicates with a borealis node at ip
    //  though the given port.
    //  Then it sends the network diagram as XML strings
    //  and runs start_query.
    //  It waits until the front-end terminates and the port is now free.
    //
    status = launchDiagram(STOCKDIST_XML);

    if (status)
    {   ERROR << "launchDiagram failed ( " << status << " ).";
    }
    else
    {   // Establish input data path connections.
        connectStock_Usd();
    }

    return  status;
}



////////////////////////////////////////////////////////////////////////////////
//
//  Connect to inputs, subscribe to outputs.
//
void  StockdistMarshal::openInputOutput()
{
//..............................................................................


    // Open a client to send and receive data.
    //
    _client = new MedusaClient(InetAddress());

    // Subscribe to outputs.
    //
    subscribeStock_Br();

    {   // Establish input data path connections.
        connectStock_Usd();
    }
    return;
}



////////////////////////////////////////////////////////////////////////////////
//
//  Activate the client I/O event loop.
void  StockdistMarshal::runClient()
{
//..............................................................................


    //  This does not return unless terminated or on an exception.
    _client->run();

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
//  Terminate the client I/O event loop.
void  StockdistMarshal::terminateClient()
{
//..............................................................................


    _client->terminate();

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
//  Copy a string value to a fixed length array and zero fill.
//
void  StockdistMarshal::setStringField(string  value,
                                       char  field[],
                                     uint32  length)
                              throw(AuroraException)
{
//..............................................................................


    if (value.length() > length)
    {   Throw(AuroraException,
              "Protocol string over " + to_string(length) + ".");
    }

    strncpy(field, value.c_str(), length);

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
void  StockdistMarshal::connectStock_Usd()
{
//..............................................................................


    // Starting to produce events on input stream.
    //
    if (!_client->set_data_path(MAX_BUFFER, Util::get_host_address("138.100.12.92"), 15000))
    {   ERROR << "Failed setting data path";
    }
    else
    {   DEBUG << "Set data path";

        _eventStock_Usd = ptr<StreamEvent>(new StreamEvent(STOCK_USD));
        _eventStock_Usd->_inject = true;
    }

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
void  StockdistMarshal::batchStock_Usd( Stock_Usd  *tuple )
{
//..............................................................................


    // Tuples are buffered in a string.
    //
    _eventStock_Usd->insert_bin(string((const char *)tuple,
                                  sizeof(Stock_Usd)));

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
void  StockdistMarshal::sendStock_Usd( uint32  sleep )
{
//..............................................................................


    // Transmit data to the node.
    Status  status = _client->fast_post_event(_eventStock_Usd);

    while (!status)
    {   if (status.as_string() == DataHandler::NO_SPACE)
        {   // Wait if no more space in buffer.
            // At this point the data was never put in the buffer.
            // It needs to be requeued unless we want to drop it.
            WARN << "We dropped a tuple.";
            Thread::sleep(Time::msecs(sleep));

            // retry (make this conditional).
            status = _client->fast_post_event(_eventStock_Usd);
        }
        else
        {   ERROR << "Connection closed... stopping event stream";
            return;
        }
    }

    if (sleep)
    {    // The event loop is activated so that the queue can be processed.
         // The callback is enqueued with a timer.
         // We only callback with a timer because this is looping.
         // We also need a delayed callback so the queue can be processed.
         // If we just go to sleep the event loop will not be run.
         //
         (new CallbackTimer(_client->get_loop(),
                             wrap(this, &StockdistMarshal::delayStock_Usd)))
                  ->arm(Time::now() + Time::msecs(sleep));

    }

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
//  Resume here after sending a tuple.
//
void  StockdistMarshal::delayStock_Usd()
{
//..............................................................................


    // Release the previous event.
    //
    _eventStock_Usd.reset();

    // Construct a new Stock_Usd input event.
    //
    _eventStock_Usd = ptr<StreamEvent>(new StreamEvent(STOCK_USD));
    _eventStock_Usd->_inject = true;

    // Return to the application code.
    //
    sentStock_Usd();

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
// Dispatch output on our fast datapath to a handler.
//
Status  StockdistMarshal::outputHandler(ptr<StreamEvent>  event)
{
//..............................................................................


    if (event->_stream == Name(STOCK_BR))
    {   return StockdistMarshal::Stock_BrHandler(event);
    }

    return  string("Unknown output stream ") + to_string(event->_stream);
}



////////////////////////////////////////////////////////////////////////////////
//
// Subscribing to receive output on a fast datapath.
//
void  StockdistMarshal::subscribeStock_Br()
{
//..............................................................................


    DEBUG << "Subscribing to receive output.";

    // Setup the subscription request.
    Status  status = _client->set_data_handler(
                                  InetAddress(Util::form_endpoint(STOCKDIST_ENDPOINT,
                                                                  DEFAULT_MONITOR_PORT)),
                                  wrap(&outputHandler));

    if (status)
    {   DEBUG << "Done subscribing to output.";
    }
    else
    {   ERROR << "Could not subscribe to output.";
    }

    return;
}



////////////////////////////////////////////////////////////////////////////////
//
// Receive output on a fast datapath.
//
Status  StockdistMarshal::Stock_BrHandler(ptr<StreamEvent>  event)
{
    StockType_BR  *tuple;
    int32         index;
    uint32        offset = 0;
//..............................................................................


    // For each tuple that was received,
    //
    for (index = 0; index < event->_inserted_count; index++)
    {
        offset += HEADER_SIZE;

        // At the tuple data past the header.
        //
        tuple = (StockType_BR *)&event->_bin_tuples[offset];
        DEBUG << "DATA:  " << to_hex_string(tuple, sizeof(StockType_BR));

        receivedStock_Br(tuple);
        offset += sizeof(StockType_BR);
    }

    // Signal done with this batch.
    //
    return  true;
}



////////////////////////////////////////////////////////////////////////////////
//
// Launch the Borealis front-end.
//
int32  StockdistMarshal::launchDiagram(string  xml)  // Path of an initial xml file.
{
    int32   status;
    string  command;
//..............................................................................


    INFO << "Connect with: " << xml;

    command = string() + "BigGiantHead  " + xml;
    status  = system(command.c_str());

    DEBUG << "Ran the Borealis front end:  " << status;

    return  status;
}

////////////////////////////  end  StockdistMarshal.cc  //////////////////////////


And have implemented some operations on the Stockdist.cpp:
///////////////////////////////////Stockdist.cpp//////////////////////////////////////////////
#include <args.h>
#include "StockdistMarshal.h"
#include <stdio.h>
#include <time.h>
#include <stdlib.h>

using namespace Borealis;

const uint32  SLEEP_TIME = 1000;

//OK
void  StockdistMarshal::receivedStock_Br(StockType_BR  *tuple)
{
	NOTICE << "Debug@receivedAggregate: before printing";	
	NOTICE << "Symbol: " << tuple->symbol;// << endl;
	NOTICE << "Time: " << tuple->time;// << endl;
	NOTICE << "Price: " << tuple->price_br;// << endl;
	NOTICE << "Debug@receivedAggregate: received Stock_Usd...";
	return;

}

//OK
void  StockdistMarshal::sentStock_Usd()
{

	Stock_Usd  tuple;
	
	tuple._data.symbol[0] = 'V';
	tuple._data.symbol[1] = 'A';
	tuple._data.symbol[2] = 'L';
	tuple._data.symbol[3] = 'E';
	tuple._data.time = 10;
	tuple._data.price_usd = 45.10;
	
	batchStock_Usd( &tuple );
	NOTICE << "Debug@sendStock_Usd: sending Stock_Usd...";	
	//NOTICE << "Debug@sendStock_Usd: tuple._data.time: " << tuple._data.time;
	//NOTICE << "Debug@sendStock_Usd: tuple._data.symbol: " << tuple._data.symbol;
	sendStock_Usd( SLEEP_TIME );
				
	return;

}


////////////////////////////////////////////////////////////////////////////////
//
int  main( int  argc, const char  *argv[] )
{
    int32           status;
    StockdistMarshal   marshal;        // Client and I/O stream state.
    status = marshal.open();

    if ( status )
    {   
        WARN << "Could not deply the network.";
    }
    else
    {

        marshal.sentStock_Usd();

        DEBUG  << "run the client event loop...";

        marshal.runClient();

    }

    return( status );
}
//////////////////////////////////////////////////////////////////////////////////////////////


So far, so good....
And the I compile and link those files with the script Compile_script_rod.sh:

#########################Compile_script_rod.sh##################################################
# --------------------------------------------------
# Script for compile Borealis example
#NB. ALL name of file must be start with uppercase character
# --------------------------------------------------

MARSHAL=Marshal
APP=app

#  echo Run marshal $1.xml
#  ${BOREALIS_HOME}/tool/marshal/marshal $1.xml

echo Compile $1$MARSHAL.cc
g++ -DHAVE_CONFIG_H -I. -I.. -I${BOREALIS}/xercesc/include   -I${BOREALIS}/nmstl/include -I${BOREALIS_HOME}/src/modules/common -I${BOREALIS_HOME}/src/modules/util -I${BOREALIS_HOME}/src/modules/rpc -I${BOREALIS_HOME}/src/modules/catalog -I${BOREALIS_HOME}/src/modules/queryProcessor -I${BOREALIS_HOME}/src/modules/queryProcessor/statsMgr -I${BOREALIS_HOME}/tool/head/  -I${BOREALIS_HOME}/utility/client/rpc/ -I${BOREALIS} -I${BOREALIS}/bdb/include -I${BOREALIS}/common/include -I${BOREALIS}/glpk/include -I${BOREALIS}/gsl/include -I${BOREALIS}/ocv/include -I${BOREALIS}/xercesc/include -I${BOREALIS}/nmstl/include/nmstl -I${BOREALIS}/nmstl/include/NMSTL -I${BOREALIS}/antlr/include -g -Wall -MT $1$MARSHAL.o -MD -MP -c -o $1$MARSHAL.o $1$MARSHAL.cc


echo Compile $1.cc
g++ -DHAVE_CONFIG_H -I. -I.. -I${BOREALIS}/xercesc/include   -I${BOREALIS}/nmstl/include -I${BOREALIS_HOME}/src/modules/common -I${BOREALIS_HOME}/src/modules/util  -I${BOREALIS_HOME}/src/modules/rpc -I${BOREALIS_HOME}/src/modules/catalog -I${BOREALIS_HOME}/src/modules/queryProcessor -I${BOREALIS_HOME}/src/modules/queryProcessor/statsMgr -I${BOREALIS_HOME}/tool/head/ -I${BOREALIS_HOME}/utility/client/rpc/ -I${BOREALIS} -I${BOREALIS}/bdb/include -I${BOREALIS}/common/include -I${BOREALIS}/glpk/include -I${BOREALIS}/gsl/include -I${BOREALIS}/ocv/include -I${BOREALIS}/xercesc/include -I${BOREALIS}/nmstl/include/nmstl -I${BOREALIS}/nmstl/include/NMSTL -I${BOREALIS}/antlr/include -g -Wall -MT $1.o -MD -MP -c -o $1.o $1.cc


echo Linking $1.o $1$MARSHAL.o
/bin/sh ${BOREALIS}/common/bin/libtool --mode=link --tag=CXX ${BOREALIS}/nmstl/bin/wtf g++ -g -Wall -R${BOREALIS}/bdb/lib -R${BOREALIS}/common/lib -R${BOREALIS}/glpk/lib -R${BOREALIS}/gsl/lib -R${BOREALIS}/ocv/lib -R${BOREALIS}/xercesc/lib -R${BOREALIS}/nmstl/lib -R${BOREALIS}/antlr/lib -o $1$app $1.o $1$MARSHAL.o -L${BOREALIS_HOME}/src/modules/common  -lborealiscommon -L${BOREALIS_HOME}/src/modules/catalog -lborealiscatalog -L${BOREALIS_HOME}/src/modules/queryProcessor -lborealisqp -L${BOREALIS_HOME}/src/external -lborealisexternal -L${BOREALIS_HOME}/src/modules/ha -lborealisha -L${BOREALIS_HOME}/src/modules/queryProcessor/expr -lborealisqpexpr -L${BOREALIS_HOME}/src/modules/queryProcessor/statsMgr -lborealisqpstatsMgr -L${BOREALIS_HOME}/src/modules/util  -lborealisutil -L${BOREALIS}/nmstl/lib -lNMSTL -lexpat -lpthread -lreadline -lncurses ${BOREALIS}/antlr/lib/libantlr.a -ldl -lcrypto -L${BOREALIS}/xercesc/lib -lxerces-c ${BOREALIS}/antlr/lib/libantlr.a -L${BOREALIS_HOME}/tool/head/ -lborealisdeploy -L${BOREALIS_HOME}/utility/client/region -lborealisregion -L${BOREALIS}/bdb/lib -ldb_cxx -ldb
##############################################################################################

And still i didn't  got any error.
Then it generates me the following script "Stockdist" and the compiled (executable) file inside the
directory "./.libs/Stockdist":

#################################Stockdist###################################################
#! /bin/bash

# Stockdist - temporary wrapper script for .libs/Stockdist
# Generated by ltmain.sh - GNU libtool 1.5.22 (1.1220.2.365 2005/12/18 22:14:06)
#
# The Stockdist program cannot be directly executed until all the libtool
# libraries that it depends on are installed.
#
# This wrapper script should never be moved out of the build directory.
# If it is, it will not operate correctly.

# Sed substitution that helps us do robust quoting.  It backslashifies
# metacharacters that are still active within double-quoted strings.
Xsed='/bin/sed -e 1s/^X//'
sed_quote_subst='s/\([\\`\\"$\\\\]\)/\\\1/g'

# The HP-UX ksh and POSIX shell print the target directory to stdout
# if CDPATH is set.
(unset CDPATH) >/dev/null 2>&1 && unset CDPATH

relink_command="(cd /home/rodrigo/software/borealis/borealis_project/Stock Distributed; LD_RUN_PATH=\"/home/rodrigo/software/borealis/software/antlr/lib:/home/rodrigo/software/borealis/software/nmstl/lib:/home/rodrigo/software/borealis/software/xercesc/lib:/home/rodrigo/software/borealis/software/glpk/lib:/home/rodrigo/software/borealis/software/gsl/lib:/home/rodrigo/software/borealis/software/bdb/lib:/home/rodrigo/software/borealis/software/mpfr/lib:/home/rodrigo/software/borealis/software/readline/lib:/home/rodrigo/software/borealis/software/expat/lib:/home/rodrigo/software/borealis/software/SDL/lib:/home/rodrigo/software/borealis/software/SDL_image/lib:/home/rodrigo/software/borealis/src/modules/common/\"; export LD_RUN_PATH; LD_LIBRARY_PATH=\"/home/rodrigo/software/borealis/software/antlr/lib:/home/rodrigo/software/borealis/software/nmstl/lib:/home/rodrigo/software/borealis/software/xercesc/lib:/home/rodrigo/software/borealis/software/glpk/lib:/home/rodrigo/software/borealis/software/gsl/lib:/home/rodrigo/software/borealis/software/bdb/lib:/home/rodrigo/software/borealis/software/mpfr/lib:/home/rodrigo/software/borealis/software/readline/lib:/home/rodrigo/software/borealis/software/expat/lib:/home/rodrigo/software/borealis/software/SDL/lib:/home/rodrigo/software/borealis/software/SDL_image/lib:/home/rodrigo/software/borealis/src/modules/common/\"; export LD_LIBRARY_PATH; PATH=\"/home/rodrigo/software/borealis/software/jdk1.5.0_16/bin:/home/rodrigo/software/borealis/tool/marshal:/home/rodrigo/software/borealis/tool/head:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/rodrigo/software/borealis/software/common/bin:/home/rodrigo/software/borealis/software/nmstl/bin:/home/rodrigo/software/borealis/software/textinfo/bin:/home/rodrigo/software/borealis/software/expat/bin:/home/rodrigo/software/borealis/software/SDL/bin:/home/rodrigo/software/borealis/software/nmstl/bin\"; export PATH; LD_RUN_PATH=\"/home/rodrigo/software/borealis/src/modules/common/.libs:/home/rodrigo/software/borealis/src/modules/catalog/.libs:/home/rodrigo/software/borealis/src/modules/queryProcessor/.libs:/home/rodrigo/software/borealis/src/external/.libs:/home/rodrigo/software/borealis/src/modules/ha/.libs:/home/rodrigo/software/borealis/src/modules/queryProcessor/statsMgr/.libs:/home/rodrigo/software/borealis/src/modules/util/.libs:/home/rodrigo/software/borealis/software/expat//lib:/home/rodrigo/software/borealis/tool/head//.libs:/home/rodrigo/software/borealis/utility/client/region/.libs:/home/rodrigo/software/borealis/software/bdb/lib:/home/rodrigo/software/borealis/software/common/lib:/home/rodrigo/software/borealis/software/glpk/lib:/home/rodrigo/software/borealis/software/gsl/lib:/home/rodrigo/software/borealis/software/ocv/lib:/home/rodrigo/software/borealis/software/xercesc/lib:/home/rodrigo/software/borealis/software/nmstl/lib:/home/rodrigo/software/borealis/software/antlr/lib:\$LD_RUN_PATH\" /home/rodrigo/software/borealis/software/nmstl/bin/wtf g++ -g -Wall -o \$progdir/\$file Stockdist.o StockdistMarshal.o  -L/home/rodrigo/software/borealis/src/modules/common /home/rodrigo/software/borealis/src/modules/common/.libs/libborealiscommon.so -L/home/rodrigo/software/borealis/src/modules/catalog /home/rodrigo/software/borealis/src/modules/catalog/.libs/libborealiscatalog.so -L/home/rodrigo/software/borealis/src/modules/queryProcessor /home/rodrigo/software/borealis/src/modules/queryProcessor/.libs/libborealisqp.so -L/home/rodrigo/software/borealis/src/external /home/rodrigo/software/borealis/src/external/.libs/libborealisexternal.so -L/home/rodrigo/software/borealis/src/modules/ha /home/rodrigo/software/borealis/src/modules/ha/.libs/libborealisha.so -L/home/rodrigo/software/borealis/src/modules/queryProcessor/expr /home/rodrigo/software/borealis/src/modules/queryProcessor/expr/.libs/libborealisqpexpr.a -L/home/rodrigo/software/borealis/src/modules/queryProcessor/statsMgr /home/rodrigo/software/borealis/src/modules/queryProcessor/statsMgr/.libs/libborealisqpstatsMgr.so -L/home/rodrigo/software/borealis/src/modules/util /home/rodrigo/software/borealis/src/modules/util/.libs/libborealisutil.so -L/home/rodrigo/software/borealis/software/nmstl/lib -lNMSTL /home/rodrigo/software/borealis/software/expat//lib/libexpat.so -lpthread -lreadline -lncurses -ldl -lcrypto -L/home/rodrigo/software/borealis/software/xercesc/lib -lxerces-c /home/rodrigo/software/borealis/software/antlr/lib/libantlr.a -L/home/rodrigo/software/borealis/tool/head/ /home/rodrigo/software/borealis/tool/head//.libs/libborealisdeploy.so -L/home/rodrigo/software/borealis/utility/client/region /home/rodrigo/software/borealis/utility/client/region/.libs/libborealisregion.so -L/home/rodrigo/software/borealis/software/bdb/lib -ldb_cxx -ldb)"

# This environment variable determines our operation mode.
if test "$libtool_install_magic" = "%%%MAGIC variable%%%"; then
  # install mode needs the following variable:
  notinst_deplibs=' /home/rodrigo/software/borealis/src/modules/common/libborealiscommon.la /home/rodrigo/software/borealis/src/modules/catalog/libborealiscatalog.la /home/rodrigo/software/borealis/src/modules/queryProcessor/libborealisqp.la /home/rodrigo/software/borealis/src/external/libborealisexternal.la /home/rodrigo/software/borealis/src/modules/ha/libborealisha.la /home/rodrigo/software/borealis/src/modules/queryProcessor/statsMgr/libborealisqpstatsMgr.la /home/rodrigo/software/borealis/src/modules/util/libborealisutil.la /home/rodrigo/software/borealis/tool/head//libborealisdeploy.la /home/rodrigo/software/borealis/utility/client/region/libborealisregion.la'
else
  # When we are sourced in execute mode, $file and $echo are already set.
  if test "$libtool_execute_magic" != "%%%MAGIC variable%%%"; then
    echo="echo"
    file="$0"
    # Make sure echo works.
    if test "X$1" = X--no-reexec; then
      # Discard the --no-reexec flag, and continue.
      shift
    elif test "X`($echo '\t') 2>/dev/null`" = 'X\t'; then
      # Yippee, $echo works!
      :
    else
      # Restart under the correct shell, and then maybe $echo will work.
      exec /bin/bash "$0" --no-reexec ${1+"$@"}
    fi
  fi

  # Find the directory that this script lives in.
  thisdir=`$echo "X$file" | $Xsed -e 's%/[^/]*$%%'`
  test "x$thisdir" = "x$file" && thisdir=.

  # Follow symbolic links until we get to the real thisdir.
  file=`ls -ld "$file" | /bin/sed -n 's/.*-> //p'`
  while test -n "$file"; do
    destdir=`$echo "X$file" | $Xsed -e 's%/[^/]*$%%'`

    # If there was a directory component, then change thisdir.
    if test "x$destdir" != "x$file"; then
      case "$destdir" in
      [\\/]* | [A-Za-z]:[\\/]*) thisdir="$destdir" ;;
      *) thisdir="$thisdir/$destdir" ;;
      esac
    fi

    file=`$echo "X$file" | $Xsed -e 's%^.*/%%'`
    file=`ls -ld "$thisdir/$file" | /bin/sed -n 's/.*-> //p'`
  done

  # Try to get the absolute directory name.
  absdir=`cd "$thisdir" && pwd`
  test -n "$absdir" && thisdir="$absdir"

  program=lt-'Stockdist'
  progdir="$thisdir/.libs"

  if test ! -f "$progdir/$program" || \
     { file=`ls -1dt "$progdir/$program" "$progdir/../$program" 2>/dev/null | /bin/sed 1q`; \
       test "X$file" != "X$progdir/$program"; }; then

    file="$$-$program"

    if test ! -d "$progdir"; then
      mkdir "$progdir"
    else
      rm -f "$progdir/$file"
    fi

    # relink executable if necessary
    if test -n "$relink_command"; then
      if relink_command_output=`eval $relink_command 2>&1`; then :
      else
	echo "$relink_command_output" >&2
	rm -f "$progdir/$file"
	exit 1
      fi
    fi

    mv -f "$progdir/$file" "$progdir/$program" 2>/dev/null ||
    { rm -f "$progdir/$program";
      mv -f "$progdir/$file" "$progdir/$program"; }
    rm -f "$progdir/$file"
  fi

  if test -f "$progdir/$program"; then
    if test "$libtool_execute_magic" != "%%%MAGIC variable%%%"; then
      # Run the actual program with our arguments.

      exec "$progdir/$program" ${1+"$@"}

      $echo "$0: cannot exec $program ${1+"$@"}"
      exit 1
    fi
  else
    # The program doesn't exist.
    $echo "$0: error: \`$progdir/$program' does not exist" 1>&2
    $echo "This script is just a wrapper for $program." 1>&2
    echo "See the libtool documentation for more information." 1>&2
    exit 1
  fi
fi
###########################################################################

So before I execute this script, I run the two Borealis nodes which is going to host
the with the command:
borealis -d 127.0.0.0:15000
borealis -d 127.0.0.0:17000

and the BigGiantHead which is where the information is going to be published and subscribed:
BigGiantHead

Then I execute the script:
./Stockdist
Just there I got error which ask me about an library that do not exist, and its is inside the 
directory of my example: "./Distributed Stock/.libs", which is created during the compilation
and it has the compiled file Stockdist.

Here the output:
------------------------------------------------------------------------------------------------
g++ -g -Wall -o /home/rodrigo/software/borealis/borealis_project/Stock Distributed/.libs/11073-lt-Stockdist Stockdist.o StockdistMarshal.o -L/home/rodrigo/software/borealis/src/modules/common /home/rodrigo/software/borealis/src/modules/common/.libs/libborealiscommon.so -L/home/rodrigo/software/borealis/src/modules/catalog /home/rodrigo/software/borealis/src/modules/catalog/.libs/libborealiscatalog.so -L/home/rodrigo/software/borealis/src/modules/queryProcessor /home/rodrigo/software/borealis/src/modules/queryProcessor/.libs/libborealisqp.so -L/home/rodrigo/software/borealis/src/external /home/rodrigo/software/borealis/src/external/.libs/libborealisexternal.so -L/home/rodrigo/software/borealis/src/modules/ha /home/rodrigo/software/borealis/src/modules/ha/.libs/libborealisha.so -L/home/rodrigo/software/borealis/src/modules/queryProcessor/expr /home/rodrigo/software/borealis/src/modules/queryProcessor/expr/.libs/libborealisqpexpr.a -L/home/rodrigo/software/borealis/src/modules/queryProcessor/statsMgr /home/rodrigo/software/borealis/src/modules/queryProcessor/statsMgr/.libs/libborealisqpstatsMgr.so -L/home/rodrigo/software/borealis/src/modules/util /home/rodrigo/software/borealis/src/modules/util/.libs/libborealisutil.so -L/home/rodrigo/software/borealis/software/nmstl/lib -lNMSTL /home/rodrigo/software/borealis/software/expat//lib/libexpat.so -lpthread -lreadline -lncurses -ldl -lcrypto -L/home/rodrigo/software/borealis/software/xercesc/lib -lxerces-c /home/rodrigo/software/borealis/software/antlr/lib/libantlr.a -L/home/rodrigo/software/borealis/tool/head/ /home/rodrigo/software/borealis/tool/head//.libs/libborealisdeploy.so -L/home/rodrigo/software/borealis/utility/client/region /home/rodrigo/software/borealis/utility/client/region/.libs/libborealisregion.so -L/home/rodrigo/software/borealis/software/bdb/lib -ldb_cxx -ldb

g++: Distributed/.libs/11073-lt-Stockdist: No such file or directory
g++: Stockdist.o: No such file or directory
g++: StockdistMarshal.o: No such file or directory
-------------------------------------------------------------------------------------------------

And each time that I execute the script the number before the -lt-Stockdist, always change.

I hope someone can help me...
I put the maximum of information, and would be very grateful if someone could help me....

P.S.: The same example it works in a Fedora Core 8 of a friend of mine... So the example is right...

thanks

---

### Post by aca_ubu on 2009-04-03
Hello Mineiro_rdf,

I just start working on this, I want to ask if you install Borealis with the software version the suggest or if you used different ones.

I got a lot of errors trying to install borealis, and there are paquetes that I can not use as they suggest, like gcc since the Ubunto version 4.3.2, The Ubuntu version that I install is Ubuntu server 8.10.

 Waiting Any reply.

---

