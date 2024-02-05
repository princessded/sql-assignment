# sql-assignment
1)What are the different crimes committed
SELECT Distinct(description)FROM `bigquery-public-data.austin_crime.crime` 

https://drive.google.com/file/d/1pefXgssBQOemdi7kRILzQhUAc5Q8rFMn/view?usp=sharing

2) Find the count of crimes commited in different districts that have not been cleared.
   
SELECT district, count(primary_type)
FROM `bigquery-public-data.austin_crime.crime` 
where clearance_status='Not cleared'
group by district

https://drive.google.com/file/d/1NC6pg-JyC7gFVl4ARgwRHxmnQlPl8zEU/view?usp=sharing

3)
SELECT bike_type,Count(bike_type) as no_of_bikes FROM `bigquery-public-data.austin_bikeshare.bikeshare_trips` 
group by bike_type

https://drive.google.com/file/d/1eDfHjGk0psdey6f9z5LKNiYXptcGpeWA/view?usp=sharing

4) Find the number of personnels in different states and arrange them in ascending order. 
SELECT state_name as State, Sum(total_hospital_unit_personnel_ft) as tot_personnel FROM `bigquery-public-data.covid19_aha.staffing` 
group by state_name
order by tot_personnel ASC

https://drive.google.com/file/d/1AOSbMakwLrQfzvnImLNDXf-KY71_pCZu/view?usp=sharing

5) Find the number of different types of complaints registered.
SELECT complaint_description, count(complaint_description) as counts FROM `bigquery-public-data.austin_311.311_service_requests` 
group by complaint_description
order by counts DESC

https://drive.google.com/file/d/1nHEi7BCsar4Ovwy8ue5NIaubAJaA3PbK/view?usp=sharing

6) Select Top 5 types of complaints whose status is still not closed.
SELECT complaint_description, count(complaint_description) as counts FROM `bigquery-public-data.austin_311.311_service_requests`
where status = 'Open'
group by complaint_description
order by counts DESC
limit 5


https://drive.google.com/file/d/13WJCCG3O57fVlRs2uBXJ324-OSytKBbO/view?usp=sharing

7) Find the data where the source of complaint for parking machine issue has been through phone
8) 
SELECT * FROM `bigquery-public-data.austin_311.311_service_requests`
where source = 'Phone' and complaint_description = 'Parking Machine Issue'
limit 50

https://drive.google.com/file/d/1xJsxh0zZ_-BVAHpf_ZT--iDlo6haLZlu/view?usp=sharing

8) Find the dates on which most number of crimes were reported along with respective crimes.
SELECT date, descript,count(date) as counts FROM `bigquery-public-data.austin_incidents.incidents_2009`
group by descript, date
order by counts Desc
limit 50

https://drive.google.com/file/d/1gI5zkVO9SuCXKf8sg7MyBeX2HORWH7A8/view?usp=sharing 

9) Find state, nursing care beds and nurnsing homes where nursing homes are greater than 40.
SELECT s.state_name, s.intermediate_nursing_care_beds, t.full_time_nursing_home_rns
FROM `bigquery-public-data.covid19_aha.hospital_beds` s
Right Join `bigquery-public-data.covid19_aha.staffing` t
on s.county_fips_code= t.county_fips_code 
where t.full_time_nursing_home_rns >40 

https://drive.google.com/file/d/1FhDbvUrKwyTAqZTRaLB_2z5T472MI9L5/view?usp=sharing

10) Find nursing care beds and nursing personnels in different states where the data for nursing beds is not missing. arrange the data in descending order with respect to nursing care beds.
    
SELECT s.state_name, s.intermediate_nursing_care_beds, t.nursing_assistive_personnel_ft
FROM `bigquery-public-data.covid19_aha.hospital_beds` s
Right Join `bigquery-public-data.covid19_aha.staffing` t
on s.county_fips_code= t.county_fips_code 
where t.full_time_nursing_home_rns >40 and s.intermediate_nursing_care_beds is Not Null 
Order by s.intermediate_nursing_care_beds DESC


https://drive.google.com/file/d/1BgWzWNd1mZAD31dJR4qAW0onTEBBF4pe/view?usp=sharing
