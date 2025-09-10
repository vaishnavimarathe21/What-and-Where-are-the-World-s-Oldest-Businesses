# What and Where are the World's Oldest Businesses

## Project Overview

This project explores the world's oldest businesses still in operation, analyzing their characteristics, geographic distribution, and industry patterns. The analysis examines data from BusinessFinancing.co.uk's research on the oldest company in almost every country to understand what enables businesses to stand the test of time.

## Background

Business longevity is a fascinating subject that reveals insights about economic resilience, cultural factors, and industry characteristics. This project investigates businesses that have survived for centuries, some even over a millennium, to understand the factors that contribute to their remarkable endurance.

## Dataset Description

### 1. `businesses.csv`
- **Purpose**: Core dataset of oldest businesses by country
- **Size**: 165+ businesses
- **Columns**:
  - `business`: Name of the business
  - `year_founded`: Year the business was established
  - `category_code`: Industry category code
  - `country_code`: ISO 3166-1 3-letter country code

### 2. `countries.csv`
- **Purpose**: Country information and geographic data
- **Size**: 195+ countries
- **Columns**:
  - `country_code`: ISO 3166-1 3-letter country code
  - `country`: Country name
  - `continent`: Continent where the country is located

### 3. `categories.csv`
- **Purpose**: Industry category definitions
- **Size**: 16 categories
- **Columns**:
  - `category_code`: Category identifier
  - `category`: Category description

### 4. `new_businesses.csv`
- **Purpose**: Additional businesses found for missing countries
- **Size**: Additional entries
- **Columns**: Same structure as `businesses.csv`

## Key Research Questions

1. **What is the world's oldest business?**
2. **Which industries produce the most long-lasting businesses?**
3. **How are these businesses distributed geographically?**
4. **What characteristics enable business longevity?**
5. **Which countries lack data on their oldest businesses?**

## Analysis Methods

### 1. Data Integration
- Merging business data with country information
- Combining category data for industry analysis
- Adding newly discovered businesses to fill gaps

### 2. Geographic Analysis
- Continent-level analysis of business distribution
- Country-specific oldest business identification
- Regional pattern recognition

### 3. Industry Analysis
- Category distribution analysis
- Industry longevity patterns
- Cross-continental industry comparisons

### 4. Temporal Analysis
- Historical distribution of business founding
- Longevity pattern identification
- Time-based trend analysis

## Key Findings

### 1. World's Oldest Business
**Kongō Gumi** (Japan, 578 AD)
- **Industry**: Construction (Temple building)
- **Age**: Over 1,400 years old
- **Location**: Japan
- **Significance**: Oldest continuously operating business in the world

### 2. Geographic Distribution

#### Oldest Business by Continent:
- **Asia**: Kongō Gumi (Japan, 578 AD)
- **Europe**: Staffelter Hof Winery (Germany, 862 AD)
- **North America**: La Casa de Moneda de México (Mexico, 1534)
- **South America**: Various businesses from 1800s
- **Africa**: Businesses from 1800s-1900s
- **Oceania**: Businesses from 1800s-1900s

### 3. Industry Analysis

#### Most Common Industries for Longevity:
1. **Banking & Finance**: Highest representation
2. **Agriculture**: Second most common
3. **Distillers, Vintners, & Breweries**: Third most common
4. **Construction**: Including the world's oldest business
5. **Cafés, Restaurants & Bars**: Including St. Peter Stifts Kulinarium (803 AD)

### 4. Historical Patterns
- **Ancient Businesses**: Primarily in Asia and Europe
- **Medieval Period**: Continued growth in Europe
- **Colonial Era**: Expansion to Americas
- **Modern Period**: Global distribution

### 5. Data Gaps
Several countries lack data on their oldest businesses:
- Various African nations
- Some Pacific island nations
- Certain Middle Eastern countries
- Some former Soviet states

## Technical Implementation

### Required Libraries
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### Key Code Snippets

#### Data Loading and Merging
```python
# Load datasets
businesses = pd.read_csv("datasets/businesses.csv")
countries = pd.read_csv("datasets/countries.csv")
categories = pd.read_csv("datasets/categories.csv")

# Merge business data with country information
businesses_countries = businesses.merge(countries, on="country_code")
```

#### Geographic Analysis
```python
# Find oldest business by continent
continent_oldest = businesses_countries.groupby("continent").agg({"year_founded":"min"})
merged_continent = continent_oldest.merge(businesses_countries, on=["continent", "year_founded"])
```

#### Industry Analysis
```python
# Merge with categories
businesses_categories = businesses.merge(categories, on="category_code")

# Count businesses by category
count_by_category = businesses_categories.groupby("category").agg({"business":"count"})
```

## Project Structure
```
What and Where are the World's Oldest Businesses/
├── datasets/
│   ├── businesses.csv
│   ├── countries.csv
│   ├── categories.csv
│   └── new_businesses.csv
├── notebook.ipynb
└── README.md
```

## Notable Businesses

### 1. Kongō Gumi (Japan, 578 AD)
- **Industry**: Construction
- **Specialty**: Temple building and maintenance
- **Significance**: World's oldest business

### 2. Staffelter Hof Winery (Germany, 862 AD)
- **Industry**: Wine production
- **Location**: Germany
- **Significance**: Oldest business in Europe

### 3. St. Peter Stifts Kulinarium (Austria, 803 AD)
- **Industry**: Restaurant
- **Location**: Austria
- **Significance**: Oldest restaurant in the world, served Mozart

### 4. La Casa de Moneda de México (Mexico, 1534)
- **Industry**: Mint/Currency production
- **Location**: Mexico
- **Significance**: Oldest business in North America

## Business Longevity Factors

### 1. Industry Characteristics
- **Essential Services**: Banking, agriculture, construction
- **Cultural Significance**: Religious institutions, traditional crafts
- **Local Monopolies**: Utilities, mints, postal services
- **Family Ownership**: Multi-generational continuity

### 2. Geographic Factors
- **Stable Regions**: Areas with consistent governance
- **Cultural Continuity**: Strong traditions and values
- **Economic Stability**: Consistent demand for services
- **Political Stability**: Avoidance of major disruptions

### 3. Business Model Factors
- **Adaptability**: Ability to evolve with changing times
- **Community Integration**: Deep roots in local communities
- **Conservative Management**: Risk-averse approaches
- **Specialized Expertise**: Unique skills and knowledge

## Insights and Implications

### 1. Industry Lessons
- **Banking & Finance**: Essential services with consistent demand
- **Agriculture**: Fundamental human need with local focus
- **Construction**: Specialized skills passed through generations
- **Food & Beverage**: Cultural and social significance

### 2. Geographic Patterns
- **Asia**: Longest business traditions, especially Japan
- **Europe**: Rich business history with diverse industries
- **Americas**: Younger business landscape with colonial influence
- **Africa**: Growing business sector with potential for longevity

### 3. Modern Applications
- **Family Business**: Multi-generational planning
- **Community Focus**: Local market specialization
- **Adaptability**: Evolution with changing times
- **Cultural Integration**: Deep community connections

## Limitations and Considerations

1. **Data Completeness**: Not all countries have complete records
2. **Definition Challenges**: What constitutes "continuous operation"?
3. **Historical Accuracy**: Some founding dates may be disputed
4. **Cultural Bias**: Western-centric business definitions

## Future Research Directions

1. **Expanded Data Collection**: Fill gaps in missing countries
2. **Industry Deep Dives**: Detailed analysis of specific sectors
3. **Failure Analysis**: Why some businesses don't survive
4. **Modern Longevity**: Analysis of 20th-21st century businesses

## Learning Outcomes

This project demonstrates:
- Data integration and merging techniques
- Geographic data analysis
- Historical data interpretation
- Business intelligence and market analysis
- Cultural and economic pattern recognition
- Data visualization for historical analysis

## Conclusion

The analysis of the world's oldest businesses reveals fascinating patterns about business longevity and success factors. Key insights include:

1. **Industry Matters**: Essential services and culturally significant businesses tend to last longer
2. **Geography Counts**: Stable regions with cultural continuity foster business longevity
3. **Adaptability is Key**: Successful businesses evolve while maintaining core values
4. **Community Integration**: Deep local roots contribute to long-term success

The project highlights the importance of understanding historical business patterns to inform modern business strategies and provides valuable insights for entrepreneurs and business leaders seeking to build lasting enterprises.

## References

- BusinessFinancing.co.uk research data
- Historical business records
- Country and continent data
- Industry classification systems
- Business longevity studies
