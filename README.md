# Node JS application

This Node.js project provides a modular interface to work with AWS DynamoDB and S3, enabling platform-specific data operations with caching and efficient query capabilities.

## 🗂️ Project Structure

---

## 🚀 Features

### DynamoDB (`dynamodbDriver.js`)
- **CRUD operations** with key-value access
- **Conditional updates** using expressions
- **Advanced filtering** for queries and scans
- **Memoized** platform-specific table name resolution
- Supports **atomic counters** and **set-type fields**

### S3 (`s3Driver.js`)
- File **upload/download** using `putObject` and `getObject`
- **Copy** and **delete** operations between buckets/keys
- Generate **signed URLs** for secure uploads
- Upload files from external **URLs** directly to S3
- Bucket resolution via platform-aware utility (`utils.resolveBucket`)

---

## 🧰 Dependencies

- `aws-sdk`
- `request`
- `stream` (Node.js core module)
- Custom modules:
  - `../globals`
  - `../memoize`
  - `../utils`

---

## ⚙️ Configuration

Ensure `globals.CURRENT_CONFIG` and related constants are properly initialized. Expected keys include:

```js
CURRENT_ENV_TYPE      // e.g., 'LOCAL' or 'PRODUCTION'
CURRENT_CONFIG = {
  aws: {
    s3: { region },
    dynamodb: {
      region,
      localEndPoint,
      tables: {
        [tableType]: {
          name,
          primaryKey
        }
      }
    }
  }
}

## 📦 Installation

```bash
npm install


globals.CURRENT_ENV_TYPE          // e.g., "LOCAL" or "PRODUCTION"
globals.ENV_TYPES                 // Environment type mappings
globals.CURRENT_CONFIG            // Contains AWS region, table config, etc.
globals.MI_TABLE_PREFIX           // Optional prefix for table naming
globals.MI_PLATFORM_TABLE         // Table for platform configuration
globals.LOGGER                    // Logging utility
