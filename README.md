# Install a IBM® WebSphere® MQ server on a Linux Ubuntu system.
## Before you begin
* Before you start the installation procedure, make sure that you have completed the necessary steps outlined in Preparing the system.
* Ensure that RPM is installed on your system, as the installation procedure uses the same RPM packages used by the other RPM based distributions. Technologies that convert these RPM packages into other forms, such as alien to convert RPMs to Debian packages, are not compatible with the IBM WebSphere MQ RPM packages and must not be used.
IBM WebSphere MQ for Linux is installed by using RPM, which is not installed by default on Ubuntu. To determine if RPM is installed on you system, use the dpkg command. For example:

``dpkg -l rpm``

If the response from this command is of the form:
``ii  rpm      4.9.1.1-1ubuntu0.1     package manager for RPM``
Then RPM is already installed on your system and no further action is required.
If the dpkg command returns output of the form:
``
$ dpkg -l rpm
No packages found matching rpm
``
Then you must install the RPM package before you install IBM WebSphere MQ. For example:
``sudo apt-get install rpm``
If this command does not complete successfully, consult your Ubuntu administrator for instructions specific to your system to install the RPM package.

## Proceed Installation
1. Run the `mqlicense.sh script`. If you want to view a text-only version of the license, which can be read by a screen reader, type the following message:
``./mqlicense.sh -text_only``

2. Install IBM WebSphere MQ. At a minimum, you must install the MQSeriesRuntime and the MQSeriesServer components.
``rpm -ivh --nodeps --force-debian MQSeriesRuntime-*.rpm``
``rpm -ivh --nodeps --force-debian MQSeriesServer-*.rpm MQSeriesJRE-*.rpm MQSeriesJava-*.rpm``
``rpm -ivh --nodeps --force-debian MQSeriesExplorer-9.0.0-0.x86_64.rpm``

3. If you have chosen this installation to be the primary installation on the system, you must now set it as the primary installation. Enter the following command at the command prompt:
``sudo /opt/mqm/bin/setmqinst -i -p /opt/mqm/``

## IBM MQ Control commands reference

* Create a new queue manager with the name "IIB10MQ"
``crtmqm  -u DLQ IIB10MQ``

* Start a queue manager or ready it for standby operation
``strmqm  -x IIB10MQ``

* Stop a queue manager or switch to a standby queue manager
``endmqm  -i IBM10MQ``

* Delete a queue manager
``dltmqm IBM10MQ``
