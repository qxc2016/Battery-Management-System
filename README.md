Battery Management System
-------------------------

This project provides software for monitoring, control and charging of batteries
for a solar powered installation.

The motivation to build this arose from the poor performance, lack of
adequate control, lack of configuration for different battery types, and poor
user interface of commercially available BMS, at least for those reasonably
priced.

The system allows for up to three batteries to be managed separately. This
ensures that failed batteries may be isolated without adversely affecting the
other batteries, as could happen if batteries were connected in parallel. Also
note that if batteries were connected in parallel, the same type and age of
battery must be used, which would necessitate changing all batteries if one were
to fail.

The system also allows for up to two loads so that critical low current loads
may be kept running after high current loads are disconnected in the event
that all batteries fall to critically low charge levels.

The system uses several methods of tracking the State of Charge of each battery,
This is a notoriously difficult parameter to estimate. In a system with three
batteries one may be isolated long enough to allow the terminal voltage to
settle to a level that will allow SoC to be computed accurately.

In the long term it is intended to allow a variety of configurations for
charging and monitoring of batteries:

1. The common three phase charger is provided using PWM to reduce the voltage
   in the absorption phase. In float phase the charger is disconnected until the
   terminal voltage drops to a threshold value. Equalization is not provided.

2. An algorithm based on Interrupted Charge Control (ICC) is also provided to
   place batteries in rest when they have reached the gassing voltage and there
   are other batteries to be charged. This has advantages of:
   (a) better utilization of the charger among the batteries,
   (b) low EMI,
   (c) reduced gas generation.

A wide range of state information is stored on a removable memory, and also
transmitted over a serial link to allow a GUI to display the state accurately
and in detail.

A GUI is provided to allow control and observation of operations. The GUI has
been provided also on a BeagleBone Black card with a LCD touchscreen. This
is suitable for wall installation and draws very low power. For wireless
communications, XBees placed in point-point AT serial mode were successful.

Each of the six interfaces has a hardware overcurrent circuit breaker and low
voltage detector, as well as providing current and voltage measurements.

A central controller based on STM32F103 controls all interfaces and the MOSFET
switches directly. Hardware signals for overcurrent and low voltage are applied
directly to the MOSFET switches for rapid disconnect.

A data processing program is also provided to generate reports of various types
from the recorded performance data.

More information is available on [Jiggerjuice](http://www.jiggerjuice.info/electronics/projects/solarbms/solarbms-overview.html).

(c) K. Sarkies 12/09/2015

TODO

1. Improvement of MOSFET switch drivers to reduce EMI at higher rates.
2. MPPT regulator for the panel.
3. Some minor system issues:
* File date error
* Communications hang when errored messages sent.


