[README.md](https://github.com/user-attachments/files/34672456/README.md)
# NYC-Rideshare-Seasonal-Demand-Patterns
**Team B06**: Melis Gurbuz (project manager), Elizabeth Lukina, Sally Hao, Taaseen Islam, Teddy Tessel

## Overview

This project analyzes **NYC Uber and Lyft** trip data from **2023–2025** to uncover when and where rideshare activity is highest, how long passengers wait, and how both change with season, location, and weather. It benchmarks **Uber against Lyft** and translates the findings into **actionable insights** for Uber's driver availability planning.

## Objectives

* Identify peak pickup periods by weekday, hour, month, and season
* Find the busiest pickup zones and compare Uber and Lyft volume
* Compare passenger wait times across platforms, hours, seasons, and zones
* Assess how daily precipitation relates to activity, waits, and fares
* Review driver pay alongside trip activity and passenger waits

## Data

* **Rideshare:** [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) – a 1% random sample of each monthly High Volume For-Hire Vehicle file, January 2023 through December 2025 (36 months, 7,155,498 trips)
* **Location:** [NYC TLC Taxi Zone Lookup Table](https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv) – pickup zone and borough names
* **Weather:** [NOAA Local Climatological Data](https://www.ncei.noaa.gov/products/land-based-station/local-climatological-data) – LaGuardia Airport daily summaries, 2023–2025 (1,096 days)
* **Key Fields:** request/pickup/drop-off time, pickup & drop-off zone, platform, trip distance and duration, base fare, driver pay, daily precipitation
* **Access:** [sampled dataset folder](https://drive.google.com/drive/folders/1B5RgYFus_WsXbsMI-O2wQXM4dcIUIt3_?usp=drive_link) and [sampling notebook](https://colab.research.google.com/drive/1wv3SVu2i7ntKiKCfwRmoRl3HJwgceg7m?usp=drive_link)

## Tools

* **Python (pandas)** – data loading, cleaning, joins & aggregation
* **Seaborn / Matplotlib** – visualization
* **Google Colab + Google Drive** – reproducible notebook workflow and data storage

## Methodology

* Combined 36 monthly samples and removed one exact duplicate
* Validated timestamps, distances, durations, fares, and driver pay; invalid measurements were excluded only from the analyses that use them, so all trips still count toward demand
* Calculated passenger wait time as pickup time minus request time
* Joined pickup zones to zone and borough names, and trip dates to daily weather (days classified as Dry or Precipitation)
* Compared seasons using average daily sampled trips to account for season length and the 2024 leap year
* Answered 15 exploratory questions, each with a hypothesis, a visualization, and a conclusion

## How to Run

1. Add the sampled dataset folder to your Google Drive.
2. Open `B06_NYC_Rideshare_Seasonal_Demand_Patterns.ipynb` in Google Colab and mount your Drive.
3. Update the `folder` variable to match the dataset's location.
4. Run the cells in order. Weather and zone files load directly from NOAA and TLC.

## Key Insights

- **Weekend evenings are the busiest periods**. Saturday 11 PM–midnight had the most pickups (71,923 sampled trips across the three years), followed by Saturday 10–11 PM (71,722).
- **Airports lead pickup activity, and Uber leads Lyft everywhere**. LaGuardia (140,733 sampled trips) and JFK (127,382) were the two busiest zones, and Uber recorded more trips than Lyft in all ten of the busiest zones.
- **Winter is growing; August is consistently the quietest month**. Average daily winter trips rose 4.35% in 2024 and 4.08% in 2025. August had the lowest daily activity in all three years, while December was far busier (about 7,132 trips per day in 2025 versus 6,217 in August).
- **Waits peak around 4 AM, not in a particular season**. Both platforms' median waits reached about five minutes around 4 AM in 2025, while seasonal medians stayed within a 15-second range (3.93–4.18 minutes).
- **Uber trails Lyft at LaGuardia in the evening**. For 5–10 mile trips at LaGuardia during 7–8 PM in 2025, Uber's median wait was 6.47 minutes versus Lyft's 4.43, even though Uber's waits were generally shorter across most hours citywide.
- **Rain barely moves waits or fares**. Median waits were 4.07 minutes on precipitation days versus 4.00 on dry days, and median base fare per mile stayed steady across both.

## Business Value

- **Driver supply:** Uber can focus driver availability on Friday and Saturday evenings, especially Saturday 10 PM–midnight, and target Quest bonuses only at zones where high demand coincides with long waits.
- **Seasonal workforce planning:** separate strategies for August and December let Uber adjust driver onboarding and incentive spending ahead of each seasonal shift.
- **Airport operations:** the LaGuardia evening gap against Lyft points to pickup coordination and driver availability as areas to investigate.
- **Dynamic pricing:** because fares and waits change little between wet and dry days, surge pricing should respond to zone-level demand spikes rather than broad weather labels.

## Limitations

- **Daily weather only:** daily summaries hide short events such as a rush-hour downpour.
- **Wet vs. dry classification:** light rain is treated the same as a severe storm or heavy snow.
- **One weather station:** LaGuardia readings stand in for every pickup zone in the city.
- **Completed trips only:** cancelled rides and unfulfilled requests are not recorded, so true demand and driver shortages cannot be measured directly.

## Conclusion

This analysis shows that NYC rideshare demand varies more by hour, location, and month than by weather, with weekend evenings, the two airports, and the winter months standing out. Uber holds a clear volume lead over Lyft, but early-morning waits and evening airport pickups at LaGuardia are areas where service can improve. These findings are starting points for Uber to investigate and test, rather than proof of driver shortages.
